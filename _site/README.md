Here’s a **README.md** tailored for Cursor to follow as a build instruction guide for your GitHub Pages Jekyll portfolio. This includes what to install, how to run the site locally, and how to structure your writing samples:

---

````markdown
# Jonathan Opperman – Technical Writing Portfolio

This is a Jekyll-based GitHub Pages site showcasing selected writing samples in QA, DevOps, and technical documentation.

## 🔧 Setup Instructions (Local Development with Cursor or Terminal)

### 1. Prerequisites

- Ruby 3.x (installed via [RubyInstaller](https://rubyinstaller.org/))
- Bundler (`gem install bundler`)
- Node.js (optional, for some content development)
- GitHub account

### 2. Install Dependencies

```bash
bundle install
````

This uses the `Gemfile` to install `github-pages` and the `just-the-docs` theme.

### 3. Run the Site Locally

```bash
bundle exec jekyll serve
```

The site will be served at:
👉 `http://localhost:4000`

### 4. Folder Structure

```
.
├── _config.yml
├── Gemfile
├── Gemfile.lock
├── index.md               # Homepage content and links to samples
├── playwright-ci-guide.md
├── shift-left.md          # (Coming soon)
├── vyos-wireguard.md      # (Coming soon)
└── assets/                # Optional images or downloads
```

---

## 📘 Writing Samples

* [CI/CD Guide: Playwright + Azure DevOps](playwright-ci-guide.md)
* [Shift-Left Testing: Why It Matters](shift-left.md) *(WIP)*
* [VyOS Quick Start: WireGuard VPN](vyos-wireguard.md) *(WIP)*

---

## 📤 Deployment via GitHub Pages1

1. Push changes to the `main` branch.
2. In repo settings, go to **Pages**.
3. Set **Source** to `GitHub Actions` or `main branch (root)`.
4. Site will be live at:
   `https://<your-username>.github.io`

---

## 💬 Contact

📫 [opperman.jonathan@gmail.com](mailto:opperman.jonathan@gmail.com)
🌍 [LinkedIn](https://www.linkedin.com/in/jonathanopperman-0a368b4a)

```