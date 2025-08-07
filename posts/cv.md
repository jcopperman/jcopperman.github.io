---
layout: page
title: Resume
nav_order: 1
parent: Resume
permalink: /posts/playwright-ci-guide/
---

# CI/CD Guide: Integrating Playwright Tests with Azure DevOps

## Overview

This guide walks you through setting up Playwright end-to-end (E2E) tests as part of your CI/CD pipeline using Azure DevOps and Docker. It assumes a basic understanding of Node.js projects and Azure Pipelines.

## Prerequisites

* Azure DevOps account with access to Pipelines
* A Git repository with a Node.js project
* Playwright tests set up locally
* Docker installed (for optional container execution)

---

## 1. Install Playwright in Your Project

```bash
npm install -D @playwright/test
npx playwright install
```

Add a basic test under `tests/example.spec.ts`:

```ts
import { test, expect } from '@playwright/test';

test('homepage loads', async ({ page }) => {
  await page.goto('https://example.com');
  await expect(page).toHaveTitle(/Example Domain/);
});
```

---

## 2. Add Playwright to Your Azure DevOps Pipeline

### Create `azure-pipelines.yml` in your repo root:

```yaml
trigger:
  branches:
    include:
      - main

pool:
  vmImage: 'ubuntu-latest'

steps:
  - task: NodeTool@0
    inputs:
      versionSpec: '18.x'
    displayName: 'Install Node.js'

  - script: |
      npm ci
      npx playwright install --with-deps
    displayName: 'Install Dependencies'

  - script: |
      npx playwright test
    displayName: 'Run Playwright Tests'

  - task: PublishTestResults@2
    inputs:
      testResultsFiles: '**/test-results/**/*.xml'
    condition: succeededOrFailed()
```

If you're using HTML reports:

```yaml
  - task: PublishPipelineArtifact@1
    inputs:
      targetPath: playwright-report
      artifact: playwright-report
      publishLocation: pipeline
```

---

## 3. (Optional) Dockerize Test Execution

Create a simple `Dockerfile`:

```dockerfile
FROM mcr.microsoft.com/playwright:v1.42.1-jammy
WORKDIR /app
COPY . .
RUN npm ci
CMD ["npx", "playwright", "test"]
```

Then add a build-and-test job in Azure DevOps if you prefer containerized runs.

---

## 4. Review Output & Artifacts

* Test output will appear in the pipeline logs
* Artifacts (HTML reports) can be downloaded via the **Pipeline Artifacts** tab
* Failures are automatically surfaced in Azure DevOps Test Reports if properly configured

---

## 5. Troubleshooting

| Issue                     | Fix                                                  |
| ------------------------- | ---------------------------------------------------- |
| Browser install fails     | Add `npx playwright install --with-deps` to pipeline |
| HTML report not rendering | Ensure report folder is published as artifact        |
| Timeout issues            | Use `timeout: 60000` in Playwright config            |

---

## Final Thoughts

This setup allows you to continuously run Playwright tests against your web app with minimal effort, scaling from simple validation to full regression testing in CI/CD. It's fast, reliable, and works great with modern development flows.

> For further customization, consider setting up parallel test shards, recording videos, or integrating Slack notifications.
