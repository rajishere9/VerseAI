**The Tech Stack We'll Use:**

*   **Static Site Generator (SSG):** **Hugo** (Super fast, easy to start with)
*   **Writing Content:** **Markdown** (Simple text format, great for code)
*   **Keeping Track of Changes:** **Git** (Essential tool for code)
*   **Storing Your Code Online:** **GitHub** (Free place to keep your Git project)
*   **Hosting Your Website (Free):** **Netlify** (Connects to GitHub, builds & hosts your site automatically)
*   **Editing Code & Content:** **VS Code** (Free, popular code editor)

**Step-by-Step Plan:**

**Phase 1: Getting Your Tools Ready (Approx. 1-2 Hours)**

1.  **Install VS Code:** If you don't have it, download and install Visual Studio Code from [https://code.visualstudio.com/](https://code.visualstudio.com/). It's a great free editor for code and text files.
2.  **Install Git:** Git keeps track of your project's history. Download and install it from [https://git-scm.com/downloads](https://git-scm.com/downloads). Just follow the default installation steps.
3.  **Install Hugo:** Hugo turns your content into a website. Go to the Hugo Releases page: [https://github.com/gohugoio/hugo/releases](https://github.com/gohugoio/hugo/releases)
    *   Find the latest release (e.g., `hugo_extended_0.XXX.X_...`). **Important:** Download the **"extended"** version for your operating system (Windows, macOS, Linux). It has better support for modern web features often used in themes.
    *   Follow the installation guide for your OS linked on the Hugo website ([https://gohugo.io/installation/](https://gohugo.io/installation/)). Often, it's just downloading a file and putting it somewhere your computer can find it (adding it to your PATH).
    *   **Verify Installation:** Open your computer's terminal or command prompt (on Windows, you can use Git Bash which came with Git, or the Command Prompt; on Mac/Linux, use Terminal) and type `hugo version`. You should see the version number printed.
4.  **Sign Up for GitHub:** Go to [https://github.com/](https://github.com/) and create a free account if you don't have one. This is where your website's code and content will live.
5.  **Sign Up for Netlify:** Go to [https://www.netlify.com/](https://www.netlify.com/) and sign up for a free account. Choose the option to **sign up with GitHub** – this makes connecting them much easier later.

**Phase 2: Creating Your Basic Blog Site (Approx. 1 Hour)**

1.  **Create Your Project Folder:**
    *   Open your terminal/command prompt.
    *   Navigate to where you want to keep your projects (e.g., `cd Documents/Projects`).
    *   Run Hugo's command to create a new site structure: `hugo new site my-coding-blog` (replace `my-coding-blog` with your desired folder name).
    *   Move into that new folder: `cd my-coding-blog`
2.  **Initialize Git in Your Project:** Still in the terminal, inside your `my-coding-blog` folder, run: `git init`. This tells Git to start tracking this folder.
3.  **Choose and Add a Theme:** Hugo needs a theme to know how the site should look.
    *   Browse themes at [https://themes.gohugo.io/](https://themes.gohugo.io/). Look for one that looks clean, is marked as responsive (works on mobile), and maybe mentions good code highlighting. Many themes have a "Demo" link.
    *   **Recommendation for Beginners:** Themes like "Ananke", "PaperMod", or "Terminal" are often good starting points.
    *   **Add the Theme (using Git Submodules - common method):** Follow the specific theme's installation instructions. It usually looks something like this (replace the URL with your chosen theme's GitHub URL):
        ```bash
        git submodule add https://github.com/theNewDynamic/gohugo-theme-ananke.git themes/ananke
        ```
    *   **Tell Hugo to Use the Theme:** Open the `hugo.toml` (or `config.toml`) file in your project folder (use VS Code!). Add this line, replacing `ananke` with the actual theme name you chose:
        ```toml
        theme = "ananke"
        ```
        *Also add a `baseURL = "/"` and `title = "My Awesome Blog"` for now. We'll change the baseURL later when Netlify gives us a URL.*
4.  **Create Your First Post:**
    *   In the terminal, run: `hugo new content posts/my-first-post.md`
    *   This creates a new Markdown file (`.md`) inside the `content/posts/` folder.
    *   **Edit the Post:** Open `content/posts/my-first-post.md` in VS Code. You'll see some lines at the top between `---`. This is called "Front Matter".
        ```yaml
        ---
        title: "My First Post"
        date: 2025-04-06T13:18:00Z  # Hugo filled this in
        draft: true  # IMPORTANT: Means it won't show up on the live site yet
        ---

        Hello World! This is my first post using **Hugo**.

        Here is some code:
        ```python
        def hello(name):
          print(f"Hello, {name}!")

        hello("Blog Reader")
        ```
        ```
    *   **Make it Visible:** Change `draft: true` to `draft: false` when you're ready for it to be seen. For now, leave it as `true` or remove the line.
5.  **Test Your Site Locally:**
    *   In the terminal, run: `hugo server -D` (The `-D` flag tells Hugo to include draft posts).
    *   Open your web browser and go to `http://localhost:1313` (or whatever address Hugo prints in the terminal).
    *   You should see your basic blog with the theme applied and your first post listed (if `draft: false` or using `-D`). Changes you make to files will often update the browser automatically!
    *   Press `Ctrl + C` in the terminal to stop the local server when done.

**Phase 3: Putting Your Blog Online (Approx. 30 Mins)**

1.  **Create a GitHub Repository:**
    *   Go to your GitHub account in your web browser.
    *   Click the "+" icon (usually top right) and select "New repository".
    *   Give it a name (e.g., `my-coding-blog`).
    *   Make sure it's set to **Public**.
    *   **Do NOT** initialize it with a README, .gitignore, or license (you already have a project locally).
    *   Click "Create repository".
2.  **Connect Local Project to GitHub:** GitHub will show you instructions. Copy the lines under "...or push an existing repository from the command line":
    ```bash
    # Make sure you are in your project folder in the terminal!
    git remote add origin https://github.com/YOUR_USERNAME/my-coding-blog.git # Replace with YOUR URL
    git branch -M main
    git push -u origin main
    ```
    *Run these commands one by one in your terminal.* You might be asked for your GitHub username/password (or token).
3.  **Add Files and Save Changes (Commit):**
    *   Before the first push, you need to tell Git which files to save:
        ```bash
        git add .
        git commit -m "Initial commit with Hugo setup and theme"
        ```
    *   Now run the `git push -u origin main` command again if you didn't already. Refresh your GitHub repository page; you should see your files there!
4.  **Deploy with Netlify:**
    *   Go to your Netlify dashboard ([https://app.netlify.com/](https://app.netlify.com/)).
    *   Click "Add new site" or "Import an existing project".
    *   Choose "Deploy with GitHub".
    *   Authorize Netlify to access your GitHub account (if you haven't already).
    *   Select the repository you just created (`my-coding-blog`).
    *   **Configure Build Settings:** Netlify is usually smart enough to detect Hugo!
        *   **Branch to deploy:** Should be `main`.
        *   **Build command:** Should automatically suggest `hugo` or `hugo --gc --minify`. Either is fine.
        *   **Publish directory:** Should automatically suggest `public`.
    *   Click "Deploy site".
5.  **Wait and Watch:** Netlify will now pull your code from GitHub, run the `hugo` command to build the site, and deploy the `public` folder contents. This might take a minute or two the first time. You'll see "Deploying..."
6.  **Visit Your Live Site!** Once it says "Published", Netlify will give you a random-looking URL (like `random-words-12345.netlify.app`). Click it! Your blog is now live online for free!
7.  **Update `baseURL`:** Copy your new Netlify URL (e.g., `https://random-words-12345.netlify.app`). Open your `hugo.toml` file and update the `baseURL` setting:
    ```toml
    baseURL = "https://random-words-12345.netlify.app/"
    theme = "ananke"
    languageCode = "en-us" # Good practice to add
    title = "My Awesome Coding Blog"
    ```
    *Save the file.*
8.  **Push the Update:** Save the `baseURL` change by committing and pushing it to GitHub:
    ```bash
    git add hugo.toml
    git commit -m "Update baseURL to Netlify URL"
    git push origin main
    ```
    *Netlify will automatically detect this push, rebuild your site, and deploy the update within a couple of minutes.*

**Phase 4: Writing Content and Making it SEO Friendly (Ongoing)**

1.  **Write New Posts:**
    *   Use the command: `hugo new content posts/another-cool-post.md`
    *   Edit the new `.md` file in `content/posts/`.
    *   Add your content using Markdown. Use code blocks (\`\`\`language ... \`\`\`) for code.
    *   Fill in the Front Matter: `title`, `date`, `description` (important for SEO!), `tags = ["coding", "python"]` etc.
    *   Set `draft: false`.
2.  **SEO Basics:**
    *   **Good Titles & Descriptions:** Write clear, descriptive titles and meta descriptions in the front matter of each post. Think about what someone would search for.
    *   **Use Headings:** Structure your posts with Markdown headings (`#`, `##`, `###`).
    *   **Image Alt Text:** If you add images (`![Alt text description](image.jpg)`), always include descriptive alt text.
    *   **Internal Linking:** Link between relevant posts on your blog.
3.  **Preview Locally:** Always run `hugo server -D` to check how things look before pushing.
4.  **Publish Changes:** When ready:
    ```bash
    git add .                  # Stage all new/changed files
    git commit -m "Added new post about XYZ" # Describe your changes
    git push origin main       # Send changes to GitHub
    ```
    *Netlify takes care of the rest automatically!*

**Phase 5: Next Steps (Optional but Recommended)**

1.  **Google Search Console:** Once your site is stable, sign up for Google Search Console ([https://search.google.com/search-console/about](https://search.google.com/search-console/about)) and add your Netlify URL. Hugo/your theme likely generates a `sitemap.xml` (e.g., `your-site.netlify.app/sitemap.xml`) - submit this URL to Google Search Console to help it find your pages.
2.  **Custom Domain:** If you want `www.yourdomain.com`, you'll need to buy a domain name (from Google Domains, Namecheap, etc. - approx $10-20/year). Then, follow Netlify's instructions to link your custom domain to your site (Netlify provides the necessary HTTPS certificate for free). This is the only potential cost.
3.  **Learn More Hugo:** Explore Hugo's documentation ([https://gohugo.io/documentation/](https://gohugo.io/documentation/)) to learn about custom layouts, shortcodes (for reusable content snippets), image processing, etc.

That's the plan! Hugo + GitHub + Netlify gives you a powerful, fast, free, and SEO-friendly platform for your coding blog, and this workflow is manageable even for beginners. Good luck!