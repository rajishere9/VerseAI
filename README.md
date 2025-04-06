# VerseAI Blog

This repository contains the source code and content for the **VerseAI** blog, available live at: **[https://verseaitech.netlify.app/](https://verseaitech.netlify.app/)**

## Overview

This blog is built using the [Hugo](https://gohugo.io/) static site generator and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme. Content is written in Markdown.

## Tech Stack

*   **Static Site Generator:** [Hugo](https://gohugo.io/) (Extended Version)
*   **Theme:** [PaperMod](https://github.com/adityatelange/hugo-PaperMod)
*   **Content Format:** Markdown
*   **Version Control:** Git
*   **Code Hosting:** GitHub
*   **Deployment & Hosting:** [Netlify](https://www.netlify.com/)

## Running Locally

To run the site locally for development or previewing changes:

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/rajishere9/VerseAI.git
    cd VerseAI
    ```
2.  **Initialize theme submodule:**
    ```bash
    git submodule update --init --recursive
    ```
3.  **Install Hugo (Extended version):** Follow the instructions at [https://gohugo.io/installation/](https://gohugo.io/installation/).
4.  **Run the Hugo development server:**
    ```bash
    hugo server -D
    ```
    The `-D` flag includes draft posts.
5.  Open your browser to `http://localhost:1313` (or the address provided by Hugo).

## Deployment

This site is automatically deployed via [Netlify](https://www.netlify.com/). Any push to the `main` branch on GitHub will trigger a new build and deployment.

*   **Build Command:** `hugo --gc --minify`
*   **Publish Directory:** `public`

## Creating Content

To add a new blog post:

1.  Use the Hugo command:
    ```bash
    hugo new content posts/your-new-post-title.md
    ```
2.  Edit the newly created Markdown file in the `content/posts/` directory.
3.  Fill in the front matter (title, date, description, tags, etc.).
4.  Set `draft: false` in the front matter when ready to publish.
5.  Commit and push the changes to the `main` branch. Netlify will handle the deployment.
