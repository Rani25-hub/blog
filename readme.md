# Blog Website Layout

**Difficulty:** Beginner  
**Primary Skills:** HTML, CSS Grid, Git  
**Dataset Source:** Self-Created Content

---

## 1. Introduction

A blog is one of the most common types of website, and almost every blog follows the same basic page structure: a header at the top, a main area for posts, a sidebar for extra information, and a footer at the bottom. This project builds that layout from scratch using **HTML** for structure and the **CSS Grid** system for positioning, with **Git** used to track and publish the work.

## 2. Problem Statement

Create a blog layout with a **header**, **sidebar**, **main content area**, and **footer** using CSS Grid. The layout must be clean, readable, and responsive so it works on desktops, tablets, and mobile phones.

## 3. Project Objective

The objective of this project is to enable students to build a blog website layout using HTML and the CSS Grid system.

By completing this project, you will learn to:

- Structure a web page with semantic HTML elements
- Create two-dimensional layouts using CSS Grid (`grid-template-areas`, `fr` units, `gap`)
- Style typography, images, and spacing
- Make a layout responsive with media queries
- Use Git to initialize, track, and push a project to a remote repository

## 4. Design Overview

### 4.1 Layout Sections

| Section      | HTML Element | Purpose                                   |
| ------------ | ------------ | ----------------------------------------- |
| Header       | `<header>`   | Blog title, tagline, and navigation links |
| Main Content | `<main>`     | List of blog posts (articles)             |
| Sidebar      | `<aside>`    | About author, categories, recent posts    |
| Footer       | `<footer>`   | Copyright and social links                |

### 4.2 Grid Plan (Desktop)

```
+----------------------------------------+
|                 HEADER                 |
+----------------------------+-----------+
|                            |           |
|        MAIN CONTENT        |  SIDEBAR  |
|        (blog posts)        |           |
|                            |           |
+----------------------------+-----------+
|                 FOOTER                 |
+----------------------------------------+
```

- **Columns:** `3fr 1fr` (main content takes 75%, sidebar takes 25%)
- **Rows:** `auto 1fr auto` (header and footer fit their content, middle grows)

### 4.3 Grid Plan (Mobile)

```
+------------------+
|      HEADER      |
+------------------+
|   MAIN CONTENT   |
+------------------+
|     SIDEBAR      |
+------------------+
|      FOOTER      |
+------------------+
```

### 4.4 Styling Choices

- **Font:** Georgia (serif) for headings, system sans-serif for body text
- **Colors:** Dark navy header/footer (`#1f2a44`), light grey page background (`#f4f5f7`), white cards for posts
- **Spacing:** Consistent `20px` grid gap and `20px` padding inside cards

### 4.5 Folder Structure

```
blog-layout/
├── index.html
├── style.css
├── images/
│   ├── post1.jpg
│   ├── post2.jpg
│   ├── post3.jpg
│   └── author.jpg
└── README.md
```

## 5. Implementation

### Step 1: Create HTML Structure

Create `index.html` with semantic elements for each section.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>My Blog</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div class="container">
      <header class="header">
        <h1>My Blog</h1>
        <p>Thoughts on code, design, and life</p>
        <nav>
          <a href="#">Home</a>
          <a href="#">About</a>
          <a href="#">Contact</a>
        </nav>
      </header>

      <main class="main">
        <!-- Blog posts go here (Step 3) -->
      </main>

      <aside class="sidebar">
        <!-- Sidebar widgets go here (Step 4) -->
      </aside>

      <footer class="footer">
        <p>&copy; 2026 My Blog. All rights reserved.</p>
      </footer>
    </div>
  </body>
</html>
```

### Step 2: Define Grid Layout

In `style.css`, turn the container into a grid and assign each section a named area.

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  display: grid;
  grid-template-columns: 3fr 1fr;
  grid-template-rows: auto 1fr auto;
  grid-template-areas:
    "header  header"
    "main    sidebar"
    "footer  footer";
  gap: 20px;
  max-width: 1100px;
  margin: 0 auto;
  padding: 20px;
  min-height: 100vh;
}

.header {
  grid-area: header;
}
.main {
  grid-area: main;
}
.sidebar {
  grid-area: sidebar;
}
.footer {
  grid-area: footer;
}
```

### Step 3: Add Blog Posts

Add self-created posts inside `<main>`. Each post is an `<article>`.

```html
<main class="main">
  <article class="post">
    <img src="images/post1.jpg" alt="Laptop on a desk" />
    <h2>Getting Started with CSS Grid</h2>
    <p class="meta">Posted on 10 October 2026 · by Author</p>
    <p>
      CSS Grid lets you build layouts in rows and columns at the same time. In
      this post, we explore how grid areas make page structure easy to read.
    </p>
    <a href="#" class="read-more">Read more →</a>
  </article>

  <article class="post">
    <img src="images/post2.jpg" alt="Notebook with code" />
    <h2>Why Semantic HTML Matters</h2>
    <p class="meta">Posted on 5 October 2026 · by Author</p>
    <p>
      Using elements like header, main, aside, and footer makes your page easier
      to read, easier to maintain, and better for accessibility.
    </p>
    <a href="#" class="read-more">Read more →</a>
  </article>

  <article class="post">
    <img src="images/post3.jpg" alt="Git branches diagram" />
    <h2>Git Basics for Beginners</h2>
    <p class="meta">Posted on 1 October 2026 · by Author</p>
    <p>
      Version control saves your progress and lets you undo mistakes. Learn the
      core commands: init, add, commit, and push.
    </p>
    <a href="#" class="read-more">Read more →</a>
  </article>
</main>
```

### Step 4: Create Sidebar

```html
<aside class="sidebar">
  <section class="widget">
    <h3>About the Author</h3>
    <img src="images/author.jpg" alt="Author photo" class="avatar" />
    <p>Hi! I'm a student learning web development and sharing what I learn.</p>
  </section>

  <section class="widget">
    <h3>Categories</h3>
    <ul>
      <li><a href="#">HTML</a></li>
      <li><a href="#">CSS</a></li>
      <li><a href="#">Git</a></li>
      <li><a href="#">Career</a></li>
    </ul>
  </section>

  <section class="widget">
    <h3>Recent Posts</h3>
    <ul>
      <li><a href="#">Getting Started with CSS Grid</a></li>
      <li><a href="#">Why Semantic HTML Matters</a></li>
      <li><a href="#">Git Basics for Beginners</a></li>
    </ul>
  </section>
</aside>
```

### Step 5: Style Typography

```css
body {
  font-family: "Segoe UI", Arial, sans-serif;
  line-height: 1.6;
  color: #333;
  background: #f4f5f7;
}

h1,
h2,
h3 {
  font-family: Georgia, "Times New Roman", serif;
  line-height: 1.3;
}

.header h1 {
  font-size: 2.5rem;
}
.post h2 {
  font-size: 1.6rem;
  margin-bottom: 8px;
}
.widget h3 {
  font-size: 1.2rem;
  margin-bottom: 10px;
}

.meta {
  font-size: 0.85rem;
  color: #777;
  margin-bottom: 12px;
}

a {
  color: #2563eb;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}
```

### Step 6: Add Images

```css
.post img {
  width: 100%;
  height: 250px;
  object-fit: cover;
  border-radius: 8px;
  margin-bottom: 15px;
}

.avatar {
  width: 100px;
  height: 100px;
  object-fit: cover;
  border-radius: 50%;
  display: block;
  margin: 0 auto 12px;
}
```

> Tip: Use free images from Unsplash or Pexels and always write meaningful `alt` text.

### Step 7: Improve Spacing

```css
.header {
  background: #1f2a44;
  color: #fff;
  padding: 30px 20px;
  text-align: center;
  border-radius: 8px;
}

.header nav a {
  color: #fff;
  margin: 0 12px;
}

.main {
  display: grid;
  gap: 20px;
}

.post,
.widget {
  background: #fff;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.08);
}

.sidebar {
  display: grid;
  gap: 20px;
  align-content: start;
}

.widget ul {
  list-style: none;
}
.widget li {
  padding: 6px 0;
  border-bottom: 1px solid #eee;
}

.read-more {
  display: inline-block;
  margin-top: 10px;
  font-weight: 600;
}

.footer {
  background: #1f2a44;
  color: #fff;
  text-align: center;
  padding: 20px;
  border-radius: 8px;
}
```

### Step 8: Apply Responsiveness

Stack everything into one column on smaller screens.

```css
@media (max-width: 768px) {
  .container {
    grid-template-columns: 1fr;
    grid-template-areas:
      "header"
      "main"
      "sidebar"
      "footer";
  }

  .header h1 {
    font-size: 2rem;
  }
  .post img {
    height: 200px;
  }
}
```

### Step 9: Test Layout

| Test                            | Expected Result                            | Status |
| ------------------------------- | ------------------------------------------ | ------ |
| Open on desktop (>1024px)       | Two columns: main and sidebar side by side | ☐      |
| Resize to tablet (~768px)       | Layout switches to one column              | ☐      |
| Open on mobile (~375px)         | No horizontal scrolling, text readable     | ☐      |
| Images load with correct sizing | No stretching or overflow                  | ☐      |
| Links hover state               | Underline appears                          | ☐      |
| Test in Chrome and Firefox      | Same appearance                            | ☐      |

Use browser **DevTools** (`F12` → Toggle Device Toolbar) to test different screen sizes. Fill in the Status column as you check each item.

### Step 10: Push to Git

**Phase 4 – Version Control workflow**

```bash
# Initialize repository
git init

# Track changes
git add .
git commit -m "Initial commit: HTML structure and grid layout"

# Commit as you progress (examples)
git add .
git commit -m "Add blog posts and sidebar"
git commit -am "Style typography and spacing"
git commit -am "Add responsive media query"

# Connect to GitHub and push
git branch -M main
git remote add origin https://github.com/<your-username>/blog-layout.git
git push -u origin main
```

**Repository link:** `https://github.com/<your-username>/blog-layout`

## 6. Features

- Clean four-section layout: header, main, sidebar, footer
- Built with CSS Grid using named `grid-template-areas`
- Semantic HTML5 structure
- Blog post cards with images, titles, dates, and excerpts
- Sidebar with author bio, categories, and recent posts
- Readable typography with a serif and sans-serif pairing
- Consistent spacing using `gap` and padding
- Fully responsive (desktop, tablet, mobile)
- Version controlled with Git

## 7. Challenges

| Challenge                                         | Solution                                                                    |
| ------------------------------------------------- | --------------------------------------------------------------------------- |
| Understanding `fr` units and grid areas           | Sketched the layout on paper first, then mapped it to `grid-template-areas` |
| Images stretching or overflowing cards            | Used `width: 100%` with `object-fit: cover`                                 |
| Sidebar stretching to full height of main content | Used `align-content: start` on the sidebar                                  |
| Layout breaking on small screens                  | Added a media query to switch to a single column                            |
| Inconsistent spacing between elements             | Applied one gap/padding value across the page                               |
| Git push rejected on first attempt                | Fixed the remote URL and used `git push -u origin main`                     |

_(Replace these with the actual challenges you faced.)_

## 8. Output

### Desktop View

![Desktop View](screenshots/desktop.png)

### Tablet View

![Tablet View](screenshots/tablet.png)

### Mobile View

![Mobile View](screenshots/mobile.png)

> Take screenshots of your finished page at each size and save them in a `screenshots/` folder.

**Live demo (optional):** Deploy for free with GitHub Pages: `https://<your-username>.github.io/blog-layout/`

## 9. Conclusion

This project demonstrated how CSS Grid makes it simple to build a classic blog layout. Named grid areas kept the structure easy to read, and a single media query was enough to make the page responsive. Along the way, the project built practical skills in semantic HTML, typography, spacing, image handling, testing, and Git version control.

**Possible future improvements:**

- Add a dark mode toggle
- Add a search bar and pagination
- Build individual post pages
- Animate hover effects on post cards
- Move from static HTML to a framework or CMS

---

## How to Run

1. Clone the repository: `git clone https://github.com/<your-username>/blog-layout.git`
2. Open the folder: `cd blog-layout`
3. Open `index.html` in any web browser

## Author

**Your Name**  
GitHub: [@your-username](https://github.com/your-username)
