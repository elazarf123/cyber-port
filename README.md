# Elazar Ferrer — IT Systems & Identity Administrator Portfolio

Personal cybersecurity and IT portfolio built with Jekyll and hosted on GitHub Pages.

🔗 **Live site:** [elazarf123.github.io/cyber-port](https://elazarf123.github.io/cyber-port/)

---

## About

This portfolio showcases hands-on labs, project write-ups, and professional documents focused on:

- **Active Directory & Identity** — AD DS, GPO, OU design, PKI/LDAPS
- **Microsoft 365 & Azure** — Entra ID, Exchange Online, Intune, PowerShell automation
- **Security** — NIST CSF/SP 800-30, security audits, vulnerability assessments, incident response
- **Systems Administration** — Windows Server 2019, DNS/DHCP, VirtualBox lab environments

## Structure

| Path | Description |
|---|---|
| `_data/projects.yml` | **Single source of truth** — lab/project entries |
| `_data/skills.yml` | **Single source of truth** — technical skill categories |
| `_data/certs.yml` | **Single source of truth** — earned and in-progress certs |
| `_posts/` | Case study and project write-ups (front-matter driven) |
| `labs/` | Detailed hands-on lab walkthroughs |
| `index.html` | Main portfolio page |
| `resume.html` | Resume download page |
| `Elazar_Ferrer_Resume IT.pdf` | Current resume |

## Running Locally

Prerequisites: Ruby ≥ 3.1 and Bundler.

```bash
bundle install
bundle exec jekyll serve
```

Then open [http://localhost:4000/cyber-port/](http://localhost:4000/cyber-port/).

## Adding or Editing Content

### Case studies / project write-ups
Posts live in `_posts/` and follow the standard Jekyll naming convention:

```
_posts/YYYY-MM-DD-short-title.markdown
```

Each post needs front matter like this:

```yaml
---
layout: post
title:  "Your Project Title"
date:   YYYY-MM-DD
img: img/portfolio/your-image.png
---
```

Write the body in Markdown below the front matter.

### Lab walkthroughs
Detailed lab write-ups live in `labs/`. Add a new Markdown (`.md`) file there and link to it from `index.html` or a post.

### Main page content
`index.html` contains the one-page portfolio layout. Edit sections directly in that file for bio, skills, and contact details.

### Site metadata
`_config.yml` holds the site title, description, social links, and color palette — update those values to change site-wide settings without touching individual pages.

### Content data files
`_data/projects.yml`, `_data/skills.yml`, and `_data/certs.yml` are the **single source of truth** for portfolio content. When Jekyll is used to build the site these files drive the templates; they also serve as structured, version-controlled documentation of current content.

## Deployment (GitHub Pages)

The repo contains a `.nojekyll` file so GitHub Pages serves the pre-built static files directly — **no build step is required**.

To deploy:
1. Push to the `master` branch (or whichever branch is set as the Pages source in the repo Settings → Pages).
2. GitHub Pages automatically picks up the changes and publishes to `https://elazarf123.github.io/cyber-port/` within a minute or two.

A GitHub Actions workflow (`.github/workflows/build.yml`) runs `bundle exec jekyll build` on every push and pull request to validate the Jekyll build still passes.

If you ever remove `.nojekyll` and want GitHub Pages to run Jekyll itself, make sure `_config.yml` has:

```yaml
url: https://elazarf123.github.io
baseurl: /cyber-port
```

(Both fields are already set correctly.)

