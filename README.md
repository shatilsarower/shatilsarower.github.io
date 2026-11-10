# Portfolio Website

A lightweight, single-page developer portfolio built with **HTML, CSS, JavaScript, Bootstrap 4, and jQuery**, and published as a static website through GitHub Pages.

The site is organized as a long-scrolling page. Its current implementation includes a hero introduction, education and technical skills, contact information, programming-contest profiles, experience details, and links to downloadable CV/resume documents.

- **Live website:** https://shatilsarower.github.io/
- **Repository:** https://github.com/shatilsarower/shatilsarower.github.io
- **Default branch reviewed:** `master`
- **Application type:** Static website
- **Build system:** None required

> [!IMPORTANT]
> **Content and ownership check required before presenting this as a personal portfolio.** The currently published HTML still contains another person's portfolio identity, biography, social profiles, contact details, education history, contest accounts, and external CV/resume links. This README describes the code currently in the repository; it does not imply that the published biography or linked documents belong to the repository owner. Replace or remove all inherited personal information before sharing the site as your own.

---

## Table of contents

- [Overview](#overview)
- [Current implementation](#current-implementation)
- [Features](#features)
- [Technology stack](#technology-stack)
- [Repository structure](#repository-structure)
- [How the website works](#how-the-website-works)
- [Run locally](#run-locally)
- [Customize the portfolio](#customize-the-portfolio)
- [Deploy with GitHub Pages](#deploy-with-github-pages)
- [Testing and verification](#testing-and-verification)
- [Known limitations and recommended fixes](#known-limitations-and-recommended-fixes)
- [Security, privacy, and maintenance](#security-privacy-and-maintenance)
- [Contributing](#contributing)
- [License and third-party assets](#license-and-third-party-assets)

---

## Overview

This repository contains a browser-based portfolio website. It does not use a server-side application, database, API layer, frontend framework, package manager, or compilation step. The browser loads `index.html`, then loads the stylesheet, image, icon, and JavaScript files referenced by that page.

The site is intended to act as a compact professional profile where a visitor can:

1. Read an introductory profile.
2. Review education and technical skills.
3. Find contact and social links.
4. Explore programming-contest and problem-solving profiles.
5. Review experience information.
6. Open the linked CV and resume documents.

The project is deliberately simple to run and host: a static web server is sufficient for local development, and GitHub Pages can serve the files without a separate application server.

## Current implementation

The active page is `index.html`. It contains the page sections and the content itself; the project does not currently separate profile data into JSON, Markdown, a CMS, or reusable frontend components.

| Page area | Current implementation | Status |
|---|---|---|
| Home / hero | Introductory heading, short biography, and hero image | Active |
| About | Education details and technical-skill progress bars | Active |
| Projects | A project showcase exists in the source as commented-out HTML | **Not rendered** |
| Contact | Static contact details and external profile links | Active |
| Experience | Contest profiles, contest history, problem-solving counts, and other experience | Active |
| CV / resume | External links to CV and resume documents | Active |
| Footer | Social links, section navigation, email, last-modified date, and page URL | Active |

The navigation currently includes a **Projects** link even though the corresponding section is commented out. Selecting that link therefore does not lead to an active project section.

## Features

### Single-page navigation

The website uses in-page anchors to move between the main sections. The navigation links use the `page-scroll` class, which is also used by the JavaScript to keep the active navigation item in sync with the visitor's scroll position.

### Introductory hero section

The hero area presents a short introduction and a profile/illustration image. The image is loaded from the local theme asset directory.

### Education and skills

The About section contains education information and a list of technical skills. Skill bars use `data-width` attributes, and the JavaScript sets the width of each `.progress_line` element when it enters the viewport.

The displayed progress-bar widths are presentation values embedded in the HTML. They should not be interpreted as independently verified proficiency scores.

### Contact and external profiles

The Contact section and footer contain static links to external communication and social-profile services. These destinations are maintained directly in `index.html`; there is no contact-form backend or message-submission service.

### Experience and contest profiles

The Experience section contains external programming-profile links and manually written contest/problem-solving information. These values are static and do not update automatically when external profile statistics change.

### CV and resume links

The CV and resume controls open externally hosted documents. The destination URLs are hard-coded in the HTML and should be checked periodically to ensure that they are still valid and publicly accessible.

### Visual effects and page behavior

The page includes a preloader, a sticky navigation style, scroll-aware active navigation, animated progress bars, and smooth scrolling behavior. These behaviors are implemented through the local JavaScript assets and CSS.

---

## Technology stack

The following technologies and libraries are referenced by the current source.

| Technology / library | Role in this project |
|---|---|
| HTML5 | Page structure and portfolio content |
| CSS3 | Theme styling, layout, responsive rules, and visual effects |
| JavaScript | Page interactions and dynamic UI behavior |
| [Bootstrap 4.3.1](https://getbootstrap.com/docs/4.3/) | Responsive grid, layout utilities, and component styling |
| [jQuery 1.12.4](https://jquery.com/) | DOM manipulation and event handling used by the theme scripts |
| [Popper.js](https://popper.js.org/) | Bootstrap 4 positioning dependency |
| [Modernizr 3.7.1](https://modernizr.com/) | Browser feature detection |
| jQuery Appear | Detects when elements enter the viewport; used by skill progress bars |
| jQuery Easing | Easing functions used by scrolling behavior |
| Scrolling Nav | Navigation/scrolling helper script |
| Animate.css | CSS animation classes referenced by the page |
| LineIcons | Icon font/classes used in the interface |
| [Font Awesome 5.8.1](https://fontawesome.com/v5) | Additional icons, loaded from an external CDN |
| Google Fonts | Montserrat and Open Sans font families, imported by the theme stylesheet |

### Dependency model

The project uses local static assets for most CSS and JavaScript dependencies. It also requests external resources at runtime:

- Font Awesome CSS from `use.fontawesome.com`.
- Google Fonts from `fonts.googleapis.com`.

A visitor needs internet access for those externally hosted resources to load. The portfolio's main HTML, theme styles, scripts, and referenced local images are stored in the repository.

### No build step

There is no frontend build pipeline in the repository's root configuration. A developer does not need to run `npm install`, `npm run build`, or a framework-specific command to serve the current site.

---

## Repository structure

The root-level repository view contains `index.html` and the nested theme directory. The following is a **runtime-oriented outline of the paths referenced by `index.html`**, not a claim that it lists every file included in the theme directory.

```text
shatilsarower.github.io/
├── index.html
└── new resume/
    └── jackson-master 2/
        └── assets/
            ├── css/
            │   ├── animate.css
            │   ├── lineicons.css
            │   ├── bootstrap.min.css
            │   ├── default.css
            │   └── style.css
            ├── images/
            │   ├── favicon.png
            │   └── hero.png
            └── js/
                ├── popper.min.js
                ├── bootstrap.min.js
                ├── jquery.appear.min.js
                ├── jquery.easing.min.js
                ├── scrolling-nav.js
                ├── main.js
                └── vendor/
                    ├── jquery-1.12.4.min.js
                    └── modernizr-3.7.1.min.js
```

### Important file responsibilities

| File or directory | Responsibility |
|---|---|
| `index.html` | Main page markup, text content, navigation, external links, and asset references |
| `assets/css/bootstrap.min.css` | Bootstrap 4.3.1 framework styles |
| `assets/css/default.css` | Theme-level default styles |
| `assets/css/style.css` | Main portfolio theme and responsive styling |
| `assets/css/animate.css` | CSS animation definitions |
| `assets/css/lineicons.css` | LineIcons icon definitions |
| `assets/images/` | Images referenced by the page, including the favicon and hero image |
| `assets/js/main.js` | Preloader, sticky navigation, active section navigation, progress bars, and page metadata display |
| `assets/js/vendor/` | Vendor scripts, including jQuery and Modernizr |
| Other files under `assets/js/` | Bootstrap and supporting scrolling/viewport scripts |

> **Path note:** The current asset paths include directory names with spaces (`new resume` and `jackson-master 2`). Those paths work as referenced by the current HTML, but they are more awkward to maintain and easier to mistype. Renaming the directories requires updating every matching `href` and `src` path in `index.html`.

---

## How the website works

### 1. Browser entry point

When a visitor opens the site, the browser requests `index.html` from the static host. The document loads the stylesheets in the `<head>` and the JavaScript files near the end of the `<body>`.

### 2. Styling and layout

Bootstrap supplies the responsive grid and layout utilities. The theme stylesheets define the visual identity of the page, including typography, spacing, section headings, buttons, hero styling, and footer styling.

### 3. JavaScript initialization

The page loads jQuery and the supporting scripts before `main.js`. The main script registers handlers for the page load and scroll events.

The current `main.js` behavior includes:

- Hiding the preloader after the window has loaded.
- Adding or removing the `sticky` class on the navigation bar based on scroll position.
- Updating the active navigation item based on the current section position.
- Closing the collapsed navigation after a navigation link is clicked.
- Animating skill progress bars when they appear in the viewport.
- Showing and hiding a back-to-top control when one is present in the markup.
- Writing the document's last-modified date and current page URL into the footer elements with IDs `modification` and `location`.

### 4. Static content

Profile text, education history, skill labels, external profile links, experience details, and document URLs are written directly in `index.html`. To update those details, edit the relevant HTML section and commit the change.

---

## Run locally

You only need Git and a local static HTTP server. No runtime installation of Node.js, npm, or a framework is required.

### Prerequisites

- Git
- Python 3 (for the example local server below), or another static file server
- A modern web browser

### Clone the repository

```bash
git clone https://github.com/shatilsarower/shatilsarower.github.io.git
cd shatilsarower.github.io
```

### Start a local server with Python

```bash
python3 -m http.server 8000
```

Open the following address in your browser:

```text
http://localhost:8000
```

Stop the server with `Ctrl + C` in the terminal.

### Alternative local servers

Any static HTTP server that serves the repository root will work. For example, PHP can serve the current directory when installed:

```bash
php -S localhost:8000
```

Using an HTTP server is preferable to opening `index.html` directly with a `file://` URL because it more closely matches how the site is served in production.

---

## Customize the portfolio

Most customization is performed in `index.html`. The existing project does not use a separate content file or admin interface.

### 1. Update the browser title and metadata

In the `<head>` section, replace the existing page title and add a meaningful meta description.

```html
<title>Your Name | Portfolio</title>
<meta
  name="description"
  content="Portfolio of Your Name, highlighting professional experience, technical skills, and selected projects."
>
```

The current description value is empty, so search engines and link previews do not receive a useful page summary from that field.

### 2. Replace the hero content

Find the section with `id="home"` and update:

- The greeting and display name.
- The short professional introduction.
- The hero image and its alternative text.

Keep the image path relative to the repository root, or update it if the image is moved.

### 3. Update education and skills

Find the section with `id="about"`. Replace the existing education details and skill labels with information that is accurate, current, and appropriate to publish.

For each skill bar, update its `data-width` value. Keep it in the range from `0` to `100` if the stylesheet/script expects a percentage. Use skill bars carefully: a visual percentage can imply a level of measurement that the page does not actually define.

### 4. Add or restore the Projects section

The source contains a project-section example, but the entire section is currently inside an HTML comment. It is therefore not rendered by the browser.

To publish projects:

1. Decide which projects are relevant to the portfolio.
2. Restore or rebuild the section with `id="projects"`.
3. Replace all demonstration project descriptions and links with verified project details.
4. Add links to source repositories and live demos where they exist.
5. Check that the Projects navigation link points to the section's actual ID.

A useful project entry normally explains the problem, the user's role, the technologies used, the important implementation decisions, and the result. Avoid listing a technology merely because it appears in a tutorial or starter template.

### 5. Update contact and social links

Find the section with `id="contact"` and the social-link lists in the hero/footer markup. Update or remove every inherited email address, telephone number, social profile, messaging handle, and university address.

Only publish contact details that the portfolio owner intends to make public. Check each destination by opening it in a browser.

### 6. Update experience and external coding profiles

Find the section with `id="experience"`. Replace the existing contest profile URLs, handles, contest history, problem-solving counts, and experience descriptions.

Counts should be current and supportable. If the statistics are not maintained, remove the counts rather than leaving stale figures on a public portfolio.

### 7. Update CV and resume documents

Find the section with `id="achievements"`. Replace the existing external document URLs with links to documents that:

- Belong to the portfolio owner.
- Are intended for public sharing.
- Do not expose private information that should not be public.
- Have permissions that allow the intended audience to view them.

Test the links in a private/incognito browser window to ensure they do not depend on the owner's signed-in session.

### 8. Replace the theme images

The current page references a favicon and hero image inside the theme's `assets/images/` directory. Replace them with appropriately sized, optimized images and update the corresponding paths if the filenames change.

Use descriptive `alt` text for meaningful images. If an image is purely decorative, use an empty `alt` attribute (`alt=""`).

### 9. Update navigation and footer labels

The header and footer contain anchor links to page sections. When adding, removing, or renaming a section, update both navigation areas so that each link points to an existing unique ID.

### 10. Keep external links safe

Links that open a new tab should include `rel="noopener noreferrer"` alongside `target="_blank"`.

```html
<a
  href="https://example.com"
  target="_blank"
  rel="noopener noreferrer"
>
  External profile
</a>
```

---

## Deploy with GitHub Pages

The repository name follows GitHub's user-site naming convention: `shatilsarower.github.io`. The site is currently reachable at:

**https://shatilsarower.github.io/**

For a standard branch-based GitHub Pages deployment, the source files should be served from the repository's deployment branch and root directory.

### Verify the Pages configuration

1. Open the repository on GitHub.
2. Go to **Settings → Pages**.
3. Check the configured build and deployment source.
4. For branch-based deployment, select the `master` branch and the `/(root)` directory if that is where the published files are maintained.
5. Save the configuration if a change is required.
6. Check the Pages deployment status and open the published URL after the deployment completes.

GitHub may take a short time to publish a new commit. The Actions/Pages deployment status is the source of truth for whether a deployment succeeded.

### Publish an update

After editing the files and verifying the site locally:

```bash
git status
git add index.html "new resume"
git commit -m "Update portfolio content"
git push origin master
```

If you add, remove, or rename other files, stage those intended changes as well. Review `git status` before committing so that unrelated files are not accidentally published.

### Deployment considerations

- The site is static; no server process needs to remain running after deployment.
- Do not commit secrets, passwords, private keys, or API tokens. Anything committed to a public repository should be treated as public.
- External fonts and icon resources may be blocked by privacy tools or network policies. The page should remain readable if those resources fail to load.
- Check the deployed page after each significant change, not only the local copy.

---

## Testing and verification

There is no automated test suite or build/test command visible in the repository's root configuration. For now, use a repeatable manual verification process before publishing.

### Functional checklist

- [ ] The home page loads without missing local assets.
- [ ] The browser title and meta description are correct.
- [ ] All header navigation links lead to existing sections.
- [ ] All footer navigation links lead to existing sections.
- [ ] The Projects link is removed or points to an active Projects section.
- [ ] The sticky navigation behaves correctly while scrolling.
- [ ] The active navigation state changes as expected.
- [ ] The preloader disappears after the page has loaded.
- [ ] Skill progress bars display their intended widths.
- [ ] The hero image and favicon load successfully.
- [ ] Every social, contact, project, CV, and resume link opens the intended destination.
- [ ] External links that open a new tab use `rel="noopener noreferrer"`.
- [ ] No inherited personal information remains unintentionally published.

### Responsive checklist

Check the page at common viewport widths, including a narrow mobile screen, a tablet-sized screen, and a desktop screen.

- [ ] Navigation remains visible and usable on mobile.
- [ ] The page does not scroll horizontally because of overflowing content.
- [ ] Text remains readable without zooming.
- [ ] Images scale within their containers.
- [ ] Buttons and links have usable touch targets.
- [ ] Long email addresses, profile URLs, and document links do not break the layout.

### Accessibility and markup checklist

- [ ] Use a logical heading hierarchy.
- [ ] Give meaningful images descriptive alternative text.
- [ ] Ensure links and controls can be reached and used with a keyboard.
- [ ] Make focus states visible.
- [ ] Use descriptive link text instead of ambiguous labels where possible.
- [ ] Do not use a `<button>` merely as a wrapper for an `<a>` element; use the appropriate interactive element directly.
- [ ] Validate the HTML and correct invalid nesting or unmatched tags.
- [ ] Check text/background contrast.

### Browser checks

At minimum, verify current versions of Chromium-based browsers, Firefox, and Safari where available. Browser rendering can differ, especially around older framework styles and externally loaded fonts.

---

## Known limitations and recommended fixes

The following items are based on the currently reviewed source and published page. They are not hypothetical future features.

| Priority | Finding | Why it matters | Recommended action |
|---|---|---|---|
| Critical | The published page still contains another person's identity and personal details | It can misrepresent the site owner and expose information that should not be associated with this repository | Replace or remove all inherited biography, contact, education, profile, and document details before presenting the site as your portfolio |
| High | The Projects section is commented out while the navigation still links to `#projects` | Visitors can select a navigation item that has no active target | Restore a real Projects section or remove the Projects links from the header and footer |
| High | The responsive navigation markup does not show a Bootstrap `.navbar-toggler` button | The collapsed navigation may not have a visible control on smaller screens | Add a correctly wired Bootstrap toggler and verify keyboard/mobile behavior |
| High | The page uses older frontend dependencies, including jQuery 1.12.4 and Bootstrap 4.3.1 | Older dependencies can have compatibility, maintenance, and security implications | Plan a tested dependency refresh; do not replace vendor files blindly |
| Medium | The page title is still `Portfolio of Asad`, and the meta description is empty | Browser tabs, search listings, and link previews can show incorrect or incomplete information | Set an accurate title and concise description |
| Medium | Several external links and document URLs are hard-coded | Links can become stale or point to the wrong person's profiles/documents | Audit and test each destination during content updates |
| Medium | New-tab links use `target="_blank"` without consistently setting `rel` | Older browser contexts may expose the opener relationship | Add `rel="noopener noreferrer"` to new-tab links |
| Medium | The `wow` animation classes and `data-wow-*` attributes are present, but no WOW.js script is loaded in the page's script list | Those attributes alone do not initialize WOW.js animations | Either load and initialize a compatible animation library or remove unused animation hooks |
| Medium | Asset paths contain spaces and deeply nested template folders | Paths are harder to maintain and more error-prone to update | Consider moving assets to a simple root-level `assets/` directory and update all references together |
| Low | Project examples remain in commented HTML | They make the source harder to read and can be mistaken for active content | Remove obsolete examples or restore only the project entries that are actually intended to be published |
| Low | Skill progress bars use manually assigned widths | Visitors may interpret decorative values as measured proficiency | Explain the scale or replace the bars with concrete evidence and project examples |
| Low | The footer dynamically prints the page URL and last-modified date | The visible values may be unnecessary and do not communicate a meaningful portfolio update history | Keep them only if they provide value; otherwise replace them with a normal copyright/ownership footer |

### Suggested improvement order

1. **Make the content accurate and safe to publish.** Replace the inherited identity, contact data, social links, and document URLs.
2. **Fix navigation and mobile usability.** Restore the Projects target or remove its link, and add a working responsive navigation toggler.
3. **Refresh the dependencies deliberately.** Verify the Bootstrap/jQuery compatibility requirements and test the page after each upgrade.
4. **Improve the portfolio content.** Publish selected projects with source links, live demos, clear descriptions, and evidence of the work completed.
5. **Add lightweight quality checks.** HTML validation, link checking, responsive browser checks, and an automated Pages deployment check would make future updates more reliable.

---

## Security, privacy, and maintenance

### Public-repository rule

A public Git repository is not a private storage location. Do not commit passwords, authentication tokens, private keys, private documents, or personal data that should not be publicly accessible.

### Personal information

The current page includes direct contact and profile information. Review every visible field and external document link before publishing. A portfolio should disclose only information that the owner has chosen to make public.

### Third-party dependencies

Some libraries are stored in the repository, while fonts and Font Awesome are loaded from third-party services. Keep a record of dependency versions and their licenses. Upgrade one dependency at a time and test navigation, layout, and JavaScript behavior after each change.

### External links

Check links periodically. Remove destinations that are no longer maintained, and make sure external pages and downloadable documents are intentionally public.

### Content maintenance

A useful maintenance routine is to review the portfolio whenever a project, role, skill, profile URL, or resume changes. Remove outdated claims rather than allowing old details to accumulate.

---

## Contributing

This repository is primarily a personal static website. Changes should preserve the lightweight deployment model unless there is a clear reason to introduce a build system or framework.

For a proposed change:

1. Create a focused branch.
2. Make the smallest relevant update.
3. Run the site locally using the instructions above.
4. Complete the functional, responsive, and privacy checklists.
5. Commit with a descriptive message and open a pull request if collaboration is enabled.

Avoid adding a dependency for behavior that can be implemented safely with the existing platform APIs.

---

## License and third-party assets

No root-level `LICENSE` file was visible in the repository view reviewed for this README. The site also includes third-party libraries and theme assets. Before redistributing the repository or reusing its theme assets in another project:

- Confirm the license of the original portfolio theme.
- Preserve required copyright and license notices.
- Confirm the licenses for Bootstrap, jQuery, Popper, Modernizr, Animate.css, LineIcons, Font Awesome, and any other bundled assets.
- Add a repository-level license only when the repository owner has the rights to license all content covered by it.

A repository license does not automatically replace the licenses of included third-party dependencies or images.

---

## Project links

- **Live website:** https://shatilsarower.github.io/
- **Source code:** https://github.com/shatilsarower/shatilsarower.github.io
- **GitHub Pages documentation:** https://docs.github.com/en/pages
- **Bootstrap 4.3 documentation:** https://getbootstrap.com/docs/4.3/
- **jQuery documentation:** https://api.jquery.com/

---

*This README documents the repository's currently observable implementation. Update it whenever the page structure, dependencies, deployment configuration, or project behavior changes.*
