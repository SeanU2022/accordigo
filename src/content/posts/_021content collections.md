---
author: "Sean Wallace"
date: 6/10/2023
image: "./images/houston_happy.4b2bc579.webp"
title: "4 Content Collections"
---

Documentation - https://docs.astro.build/en/guides/content-collections/
Sample Blog Posts - https://github.com/jamesqquick/astro-course-demo/tree/main/src/content/posts
Sample Images - https://github.com/jamesqquick/astro-course-demo/tree/main/public/images

## 🚀 Add directories:-

pubic/images/*.pn/jpgg files
src/content/posts/*.md files
src/content/config.ts

```text
/
├── public/
│   │   ├── images/
...
├── src/
│   ├── content/config.ts
│   │   ├── _posts_template/
│   |   │   └── _blog_template(the template for live post files).mdx
│   │   ├── posts/
│   │   │   ├── images/
│   │   └── post(the live post files).mdx
...
```
## 🚀 config.ts

the collection Must be the same name as "posts" directory in the code:-
```
// 1. Import utilities from ‘astro:content'
import { defineCollection } from "astro:content";

// 2. Define your collection(s)
const postsCollection = defineCollection({
// 
})

// 3. Export a single 'collections' object to register your collection(s)
// This key should match your collection directory name in "src/content"
export const collections = {
    posts: postsCollection,
}
```