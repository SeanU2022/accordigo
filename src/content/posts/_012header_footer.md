---
author: "Sean Wallace"
date: 26/9/2023
image: "./images/houston_happy.4b2bc579.webp"
title: "1 Header/Footer"
---

## 🚀 Header Footer basic setup
The CSS is very important here 

```text
/
├── public/
│   └── favicon.svg
│   └── heartbeat.png
├── src/
│   ├── components/
│   │   └── Header.astro
│   │   └── Footer.astro
```
## import Header/Footer into Layout.astro and use them:-
---
import Header from '../components/Header.astro';
import Footer from '../components/Footer.astro';
import '@fontsource/cabin';
interface Props {
	title: string;
}

const { title } = Astro.props;
---
~~~
THIS IS Header.astro:
<!doctype html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta name="description" content="Astro description" />
		<meta name="viewport" content="width=device-width" />
		<link rel="icon" type="image/svg+xml" href="/favicon.svg" />
		<meta name="generator" content={Astro.generator} />
		<title>{title}</title>
	</head>
	<body class="min-h-screen grid grid-rows-[auto,1fr,auto]">
		<Header/>
		<slot />
		<Footer />
	</body>
</html>
~~~

## change index.astro to this:-
---
import Layout from '../layouts/Layout.astro';
---
```
In index.astro all we do is inline CSS
<Layout title="Welcome to Astro.">
	<main class="px-24 max-sm:px-5 max-w-7xl mx-auto w-full">
		<h1 class="text-6xl text-teal-800 font-bold mb-5">Rhythm Nation Blog</h1>
			<p class="text-zinc-900 text-2xl mb-24 max-sm:mb-14">
				Join the community and learn from Music Producers and Enthusiasts
			</p>
			<hr class="w-full border border-teal-900 mb-16 max-sm:mb-10">
	</main>
</Layout>
```
