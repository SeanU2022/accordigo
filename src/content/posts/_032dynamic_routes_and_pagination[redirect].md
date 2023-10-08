---
author: "Sean Wallace"
date: 6/10/2023
image: "./images/houston_happy.4b2bc579.webp"
title: "_032dynamic_routes_and_pagination[redirect]"
---
# 🧑‍🚀 Fixing the problem of blog/1 and blog being duplicates!!! 

# 🚀 In astro.config.mjs use redirect!
https://docs.astro.build/en/core-concepts/routing/#redirects

export default defineConfig({
  redirects: {
    '/blog': '/blog/1'
  }
});

this way:
the blog.astro becomes obsolete since when you go 
localhost/blog it goes to localhost/blog1 with pagination
