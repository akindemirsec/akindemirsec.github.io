# Quick Start Guide

This guide will help you quickly get started with this Jekyll portfolio site.

## 📦 Installation

### Step 1: Install Ruby

**Windows:**
Download and install from [RubyInstaller](https://rubyinstaller.org/)

**macOS:**
```bash
brew install ruby
```

**Linux (Ubuntu/Debian):**
```bash
sudo apt-get install ruby-full build-essential
```

### Step 2: Install Bundler

```bash
gem install bundler
```

### Step 3: Install Dependencies

```bash
bundle install
```

## 🚀 Running Locally

Start the development server:

```bash
bundle exec jekyll serve
```

Then open http://localhost:4000 in your browser.

## 📝 Creating a New Blog Post

1. Create a new file in `_posts/` directory
2. Use format: `YYYY-MM-DD-title-slugified.md`
3. Add frontmatter:

```markdown
---
layout: post
title: "Your Post Title"
date: 2024-06-15
categories: [category1, category2]
tags: [tag1, tag2, tag3]
excerpt: "Brief excerpt shown in blog list"
---

Your content here using Markdown...
```

4. Save and the site will automatically rebuild

## 📂 Project Structure

```
.
├── _config.yml           # Site configuration
├── _includes/            # HTML components
│   ├── nav.html         # Header/navigation
│   └── footer.html      # Footer
├── _layouts/            # Page templates
│   ├── default.html     # Base layout
│   ├── post.html        # Blog post layout
│   └── page.html        # Regular page layout
├── _posts/              # Blog articles (YYYY-MM-DD-title.md)
├── assets/
│   ├── css/
│   │   └── style.css    # Main stylesheet
│   └── images/          # Images
├── about.md             # About page
├── blog.md              # Blog listing page
├── contact.md           # Contact page
├── projects.md          # Projects page
└── index.md             # Homepage
```

## 🎨 Customizing the Site

### Change Site Title & Description

Edit `_config.yml`:
```yaml
title: Your Site Title
description: Your site description
author: Your Name
```

### Change Colors

Edit `assets/css/style.css`:
```css
:root {
  --primary-color: #1e40af;      /* Change this color */
  --text-color: #1f2937;
  --bg-color: #ffffff;
}
```

### Change Avatar

Replace `akn-avatar.png` with your own image (keep the same name).

### Add a New Menu Item

Edit `_includes/nav.html` and add to the nav-links list:
```html
<li><a href="{{ '/your-page' | relative_url }}">Your Page</a></li>
```

Then create `your-page.md`:
```markdown
---
layout: page
title: "Your Page Title"
permalink: /your-page/
---

Content here...
```

## 🚢 Deploying to GitHub Pages

1. Create repository named `yourusername.github.io`
2. Push your code to GitHub
3. Go to Settings > Pages
4. Select "Deploy from a branch"
5. Choose "main" branch
6. Your site will be live at https://yourusername.github.io

See [GitHub Pages Deployment Guide](/_posts/2024-05-10-github-pages-deployment.md) for detailed steps.

## 🔧 Troubleshooting

### "bundle: command not found"
```bash
gem install bundler
```

### "Cannot find jekyll"
```bash
bundle install
bundle exec jekyll serve
```

### Port 4000 already in use
```bash
bundle exec jekyll serve --port 4001
```

### Changes not showing
1. Stop server (Ctrl+C)
2. Run `bundle exec jekyll serve` again
3. Hard refresh browser (Ctrl+Shift+R)

### Build errors
Check `_config.yml` for YAML syntax errors. Use online YAML validator if needed.

## 📚 Useful Commands

```bash
# Serve with live reload
bundle exec jekyll serve --livereload

# Build without serving
bundle exec jekyll build

# Build with future posts
bundle exec jekyll serve --future

# Build with drafts
bundle exec jekyll serve --drafts

# Watch for changes without serving
bundle exec jekyll build --watch

# Clean build
bundle exec jekyll clean
bundle exec jekyll build
```

## 🔗 Useful Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages Docs](https://docs.github.com/en/pages)
- [Markdown Guide](https://www.markdownguide.org/)
- [YAML Format](https://yaml.org/)
- [Liquid Templates](https://shopify.github.io/liquid/)

## 📝 Writing Tips

### Front Matter Examples

Blog post:
```markdown
---
layout: post
title: "My Blog Post"
date: 2024-06-15
categories: [security, devops]
tags: [docker, security, kubernetes]
excerpt: "Summary for blog list"
---
```

Page:
```markdown
---
layout: page
title: "About"
permalink: /about/
---
```

### Markdown Features

```markdown
# Heading 1
## Heading 2
### Heading 3

**Bold text**
*Italic text*

- Bullet point
- Another point

1. Numbered item
2. Another item

> Blockquote

[Link text](https://example.com)

![Image alt text](image-path.jpg)

`inline code`

\`\`\`python
# Code block
print("Hello")
\`\`\`

| Table | Header |
|-------|--------|
| Cell  | Cell   |
```

## 🎯 Next Steps

1. Customize `_config.yml` with your info
2. Replace avatar image
3. Update About page
4. Add your first blog post
5. Deploy to GitHub Pages
6. Share your site!

## 💡 Pro Tips

- Use categories to organize posts by topic
- Use tags for fine-grained filtering
- Write clear excerpts for better blog list
- Keep the "Last Updated" date in README
- Test posts locally before publishing
- Use descriptive commit messages

---

**Happy blogging! 🚀**

For questions or help, check the main [README.md](README.md) or the [GitHub Pages Deployment Guide](/blog/).
