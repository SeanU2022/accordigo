---
author: "Sean Wallace"
date: 6/10/2023
image: "./images/houston_happy.4b2bc579.webp"
title: "3 Markdown and Frontmatter"
---


## 🚀 Markdown
Used for blog posts newsletters etc
https://www.markdownguide.org/getting-started/
https://stackedit.io/app#

Astro has first class support for MD, MDX, yaml, json etc

The two folders used in Astro are content and pages.
use pages for quick rendering
use content for the real action
https://docs.astro.build/en/guides/integrations-guide/mdx/

# Quck install Using NPM
npx astro add mdx


```text
/
├── public/
│   └── favicon.svg
...
├── src/
│   ├── content/
│   │   ├── _posts_template/
│   |   │   └── _blog_template(the template for live post files).mdx
│   │   ├── posts/
│   │   │   ├── images/
│   │   └── post(the live post files).mdx
...
│   └── pages/
│       └── index.astro
│       └── bootstrap.md
└── package.json
```
## 🚀 Frontmatter

Key value pairs in md / mdx files like this:

---
title: About Page
date: 5/10/2023
image: /images/photoshoot.png
featured: false
author: sean-wallace
---