# Akın Demir's Portfolio & Blog

Welcome to my GitHub Pages portfolio and blog! This is where I share insights, research, and learning materials on cybersecurity, digital forensics, and DevSecOps.

## 👋 About

I'm **Akın Demir**, a DFIR & Cyber Security Analyst at DIFOSE LLC and part-time Forward Deploy Engineer at Binalyze. This site documents my journey in cybersecurity with a focus on:

- 🔍 **Digital Forensics & Incident Response (DFIR)**
- 🛡️ **Security Operations & SIEM**
- 🐳 **DevSecOps & Container Security**
- 🦠 **Malware Analysis**
- 🎯 **CTF Write-ups & Security Research**

## 📚 Blog Categories

### Forensics
- Memory forensics using Volatility
- MemLabs CTF write-ups
- Digital forensics techniques
- Timeline analysis

### DevSecOps
- Jenkins pipeline configuration
- Docker security & container hardening
- CI/CD security integration
- Infrastructure as Code scanning

### Malware Analysis
- Malware analysis fundamentals
- Static and dynamic analysis
- Reverse engineering techniques
- Malware family analysis

## 🛠️ Technologies & Skills

**Languages:** Python, Java, Django, React, React Native, Swift (iOS), Android

**Security Focus:** SIEM, Digital Forensics, Incident Response, Threat Hunting, Malware Analysis

**Tools & Platforms:** Docker, Linux, Volatility, Jenkins, PostgreSQL, MySQL

## 📖 Getting Started

### View the Blog

Visit the deployed site at: [https://akindemirsec.github.io](https://akindemirsec.github.io)

Or locally:
```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000

### Explore Content

- **[Home](/)** - Latest posts and overview
- **[Blog](/blog/)** - All blog posts organized by date
- **[About](/about/)** - Professional background and expertise
- **[Projects](/projects/)** - Featured projects
- **[Contact](/contact/)** - Get in touch

## 🔗 Connect

- **GitHub:** [@akindemirsec](https://github.com/akindemirsec)
- **LinkedIn:** [Akın Demir](https://linkedin.com/in/akindemirsec/)
- **Twitter/X:** [@0x52sh3ll](https://twitter.com/0x52sh3ll)
- **Email:** akindemirsec@gmail.com

## 🏆 Certifications

- **Certified Security Operations Analyst (CSOA)** - Hackviser
- **Introduction to Cybersecurity** - Cisco Networking Academy

## 📋 Project Structure

```
.
├── _config.yml              # Jekyll configuration
├── _includes/               # Reusable HTML components
│   ├── nav.html            # Navigation header
│   └── footer.html         # Footer
├── _layouts/               # HTML layouts
│   ├── default.html        # Base layout
│   ├── page.html           # Page layout
│   └── post.html           # Blog post layout
├── _posts/                 # Blog posts
├── assets/
│   ├── css/
│   │   └── style.css       # Main stylesheet
│   └── images/
├── about.md                # About page
├── blog.md                 # Blog listing
├── contact.md              # Contact page
├── projects.md             # Projects page
└── index.md                # Homepage
```

## 🚀 How to Run Locally

### Prerequisites
- Ruby 2.7 or higher
- Bundler

### Setup
```bash
# Clone or navigate to the repository
cd github_pages

# Install dependencies
bundle install

# Serve locally
bundle exec jekyll serve
```

Visit http://localhost:4000 in your browser.

## ✍️ Writing Blog Posts

To add a new blog post:

1. Create a file in `_posts/` with format: `YYYY-MM-DD-post-title.md`
2. Add YAML frontmatter:

```markdown
---
layout: post
title: "Your Post Title"
date: 2024-XX-XX
categories: [category1, category2]
tags: [tag1, tag2, tag3]
excerpt: "Brief excerpt of your post"
---

Your content here...
```

3. Commit and push to main branch
4. GitHub Pages will automatically rebuild

## 🎨 Customization

### Change Theme
Edit `_config.yml`:
```yaml
theme: minima
# or other Jekyll themes
```

### Customize Colors
Edit `assets/css/style.css` and modify CSS variables in `:root`.

### Add New Pages
Create `.md` file in root directory with frontmatter:
```markdown
---
layout: page
title: "Your Page Title"
permalink: /custom-path/
---

Content here...
```

## 🔒 Security

- This site is static (no backend/database)
- No user data collection
- No cookies or tracking
- Open source and transparent

## 📄 License

Content is licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) - feel free to use and share with attribution.

Code snippets are licensed under MIT.

## 🤝 Contributing

Found an error or have suggestions? Feel free to:
- Report issues on GitHub
- Submit pull requests
- Reach out via email or social media

## 📚 Resources & References

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [GitHub Pages](https://pages.github.com/)
- [Markdown Guide](https://www.markdownguide.org/)
- [OWASP](https://owasp.org/)
- [MemLabs](https://github.com/stuxnet999/MemLabs)
- [Volatility](https://www.volatilityfoundation.org/)

## 🎓 Learning Path

New to cybersecurity? Here's a suggested reading order:

1. Start with [Malware Analysis Fundamentals](/blog/2024/04/01/malware-analysis-fundamentals/)
2. Learn [File Hashing & Identification](/blog/2024/03/20/file-hashing-identification/)
3. Explore [Volatility Reference Guide](/blog/2024/02/15/volatility-command-reference/)
4. Try the [MemLabs Challenge 0 Writeup](/blog/2024/01/12/memlabs-challenge-0-writeup/)
5. Study [DevSecOps Pipeline Building](/blog/2024/02/28/devsecops-pipeline-jenkins/)

---

**Last Updated:** June 2024

*Happy learning and security research! 🔐*
