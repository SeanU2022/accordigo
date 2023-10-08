---
author: "Sean Wallace"
date: 26/9/2023
image: "./images/houston_happy.4b2bc579.webp"
title: "1 Astro Basic Structure"
---

Bootstrap

## 🚀 Setup
nvm use 18
node -v {must be 18.14^}
npm create astro@latest
cd [project folder]
npx astro add tailwind
mkdir -p src/content/posts/images
mkdir -p src/content/_posts_template
touch src/content/_posts_template/_blog_template.mdx
manually create _blog_template.mdx
manually create pages/bootstrap.md
manually create posts/_01_setup_and_structure.md (this file)
install https://marketplace.visualstudio.com/items?itemName=SheltonLouis.astro-snippets
npm run dev
go to URL http://localhost:4321/bootstrap

npm install @fontsource/cabin
update tailwind.config.cjs:
const defaultTheme = require('tailwindcss/defaultTheme')
and:-
  extend: {
			fontFamily: {
				sans: ['Cabin', ...defaultTheme.fontFamily.sans],
			},
  },
and in Layout.astro use the new font:-
  import '@fontsource/cabin';

## 🚀 Project Structure

Inside THIS Astro project, you'll see the following folders and files and you will create `src/content/posts` and `src/content/_posts_template` the underscore tells Astro to ignore:

```text
/
├── public/
│   └── favicon.svg
├── src/
│   ├── components/
│   │   └── Card.astro
│   ├── content/
│   │   ├── _posts_template/
│   |   │   └── _blog_template(the template for live post files).mdx
│   │   ├── posts/
│   │   │   ├── images/
│   │   └── post(the live post files).mdx
│   ├── layouts/
│   │   └── Layout.astro
│   └── pages/
│       └── index.astro
│       └── bootstrap.md
└── package.json
```

Astro looks for `.astro` or `.md` files in the `src/pages/` directory. Each page is exposed as a route based on its file name. NOTE: while `.md` works here they are better in the `src/content/posts` ...see below.

There's nothing special about `src/components/`, but that's where we like to put any Astro/React/Vue/Svelte/Preact components.

Version 2: Any static assets, like images, can be placed in the `public/` directory.

Version 3: We will manually create `src/content/posts` to contain `.md` and `.mdx` and `image [png, jpeg, webp etc]` files for a blog.


## components/.astro files
`---`
  FRONT MATTER: javascript goes here
  interface Props { for example }
`---`
```
  <html tags>
    <main>
    ...
    </main>
  </html tags>
  <styles for this page/component only>
    ...
  </styles for this page/component only>
```

## pages/index.astro etc
Astro follows paged based routing

## Layout.astro
  The root for all .astro files
  The slot is where all .astro components get rendered
`---`
  FRONT MATTER: javascript goes here
  interface Props { for example }
`---`
```
  <html tags>
    	<body>
		      <slot /> ==> everything between <main>..</main> goes here
	    </body>
  </html tags>
  <style is:global>
    ...these will be for all components
  </style>
```


## Config files
  astro.config.mjs 
      => you can set port here
      => default port v2 3000
      => default port v3 4321
  tailwind.config.cjs



