# ExciteStem Website

Welcome to the ExciteStem website project! This is a complete, multi-page static website built to be extremely fast, fully accessible, and easily hosted on GitHub Pages for free.

## The Technology Stack
**We are using [Astro](https://astro.build/)**.
**Why?** Astro is a modern static site builder that allows us to create reusable pieces of a website (like a Header and Footer) so you don't have to copy and paste them onto every single page. However, unlike heavy application frameworks, Astro outputs 100% plain, lightning-fast HTML and CSS. The code inside Astro files looks exactly like standard HTML, making it very easy for non-developers to edit.

## How to Run the Site on Your Computer
To see the site locally and make changes:
1. Open a terminal in this folder.
2. Install dependencies (only needed the first time): `npm install`
3. Start the local server: `npm run dev`
4. Open your browser to the local URL (usually `http://localhost:4321`).
5. (Optional) To build the final static HTML files to a `dist/` folder, run `npm run build`.

## Customizing the Website

### 1. Changing Colors, Fonts, and Spacing (The Theme)
All of the site's visual styling is controlled by a single file: `src/styles/theme.css`.
Open this file, and right at the top you will see a list of `--color-primary`, `--font-family-base`, and other variables. Change the hex codes (e.g., `#4caf50`) to your brand colors, save the file, and the entire site will instantly update!

### 2. Changing Images
All images are stored in the `public/images/` folder. Currently, they are filled with placeholder SVGs. To replace them, simply drop your own image files into this folder and give them the exact same name to overwrite the placeholders.
- `logo.svg`: The logo in the top-left of the header.
- `hero-students.svg`: The main image on the Home page.
- `about-teaser.svg`: The image next to "Our Mission" on the Home page.
- `about-story.svg`: The image on the About Us page.
- `avatar-1.svg` through `avatar-4.svg`: The headshots for the testimonials and team members.
- `partner-1.svg` through `partner-8.svg`: The logos in the partner showcase.
- `map-placeholder.svg`: The map on the Contact page.

### 3. Editing Text Content
Open the files inside the `src/pages/` folder:
- `index.astro` (Home page)
- `about.astro` (About Us page)
- `contact.astro` (Contact Us page)
Look for the HTML comments that say `<!-- REPLACE: ... -->`. The actual text is right below these comments. You can edit the text exactly as if it were a standard HTML file or Word document text.

### 4. Adding New Content (Testimonials, Team Members, Partners)

**To add a new Testimonial:**
1. Open `src/components/TestimonialSlider.astro`.
2. At the very top, you'll see a list inside `const testimonials = [ ... ]`.
3. Copy one of the blocks wrapped in `{ ... }` and paste it at the end of the list, separated by a comma.
4. Update the `quote`, `name`, `role`, and `avatar` text inside the new block.

**To add a new Team Member:**
1. Open `src/pages/about.astro`.
2. Near the top, find the `const team = [ ... ]` array.
3. Add a new block for the team member just like you did for the testimonials, providing `name`, `title`, `bio`, and `image`.

**To add a new Partner Logo:**
1. Drop the new logo image into `public/images/`.
2. Open `src/components/PartnerLogos.astro`.
3. The simplest way is to manually replace the `<div class="logo-item">...</div>` grid with standard HTML tags linking to your new logos. The current placeholder uses a loop for convenience, but you can safely delete the loop (`{logos.map(...) }`) and write out your `<img src="/images/your-logo.png" />` tags individually inside the `<div class="logo-grid">`.

### 5. Activating the Contact Form
GitHub Pages cannot process form submissions directly, so we're using a static-friendly service.
1. Sign up for a free account at [Formspree](https://formspree.io/).
2. Create a new form and copy your unique Formspree URL.
3. Open `src/pages/contact.astro`.
4. Find the `<form action="...">` tag and replace the URL inside `action=""` with your Formspree URL.

## Deploying to GitHub Pages

This project is set up to deploy completely automatically!

1. **Push your code:** Commit all your files and push them to a repository on GitHub.
2. **Check the Action:** In your GitHub repository, we have included a file (`.github/workflows/deploy.yml`). This tells GitHub Actions to build your Astro site every time you push to the `main` branch.
3. **Enable GitHub Pages settings:** 
   - Go to your repository's **Settings** tab.
   - Click on **Pages** in the left sidebar.
   - Under "Build and deployment", set the **Source** to **GitHub Actions**.
4. **Wait a minute:** It usually takes 1–3 minutes for the action to run. Once it finishes, your site will be live! The exact URL will be displayed in the Settings > Pages tab.

*Note: If you deploy to a repository that isn't your main `username.github.io` (for example, `username.github.io/reponame`), you must open `astro.config.mjs` and set the `base: '/reponame'` option so that images and links load correctly.*
