---
author: "Sean Wallace"
date: 6/10/2023
image: "./images/houston_happy.4b2bc579.webp"
title: "5 Content Collections configuration with ZOD"
---
https://docs.astro.build/en/guides/content-collections/

https://docs.astro.build/en/guides/content-collections/#defining-a-collection-schema

Zod Documentation - https://zod.dev/

Date Fns - https://date-fns.org/

## 🚀 make sure:-
npm install date-fns

## 🚀 inside config.ts:-

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
## 🚀 define a collection schema

inside config.ts the schema matches the frontmatter value pairs


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