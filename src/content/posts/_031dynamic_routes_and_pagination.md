---
author: "Sean Wallace"
date: 6/10/2023
image: "./images/houston_happy.4b2bc579.webp"
title: "_031dynamic_routes_and_pagination"
---

# 🚀 Creating Dynamic Routes for Blog Posts
Dynamic Routes - https://docs.astro.build/en/core-concepts/routing/#dynamic-routes

For SSR with dynamic routing create: THE BLOG PAGE LAYOUT: src/pages/blog/[slug].astro
This dynamically generates each page for each blog post
In src/pages/blog/[slug].astro Key Code is:
```
---
==> GET THE POSTS COLLECTION THAT WE CREATED EARLIER
import { getCollection } from "astro:content"

==> WE GO THROUGH POSTS ARRAY WITH MAP
==> AND USING PARAMS WE GET THE SLUG
==> AND USING PROPS WE GET THE POST ITSELF

export const getStaticPaths = async () => {
  const posts = await getCollection("posts");
  
  const paths = posts.map(post=> {
    return {
      params: {
        slug: post.slug
      },
      props: {
        post
      }
    }
  })
  return paths;
}

==> HERE WE DESTRUCTURE THE POST FROM PROPS ABOVE
==> AND DISPLAY DATA FROM THE POST PASSED IN 

type Props = {
    post: CollectionEntry<"posts">
}

const {post} = Astro.props;
---
//  note: this is the html section and above is JS section with: ---
{post.data.title}


```


# 🚀 Displaying Blog Posts.mp4
Add H1, Header, Main .astro and use in src/pages/blog/[slug].astro
==> THIS RENDERS THE BLOG FOR US
const {Content, headings} = await post.render();
==> IN Main.astro it has a slot like Layout.astro
==> this gets used to get to /Content in the [slug]

# 🚀 Styling Blog Posts Using The Tailwind Typography Plugin.mp4
This is the easiest way to style up md files:-
Tailwind Typography Plugin - https://tailwindcss.com/docs/typography-plugin
npm install -D @tailwindcss/typography
tailwind.config.cjs plugins...
    require('@tailwindcss/typography'),

and in the slug file we use tw:
```
      <div class="prose prose-2xl overflow-visible relative mb-20">
        <Content/>
      </div>
```

# 🚀 Cleaning Up Code With Reusable Compon...
Make sure all the pages import Layout H1 and Main and use those 3 components

# 🚀 Creating the TableOfContents Componen...
Create PostTOC.astro which uses MarkdownHeading
NOTE: <nav class="max-lg:hidden"> hides TOC on small screens
NOTE: in slug here is TOC in flex next to content:
```
      <div class="relative flex gap-x-12">
        <div class="prose prose-2xl overflow-visible relative mb-20">
          <Content/>
        </div>
        <PostTOC headings={headings} />
      </div>
```
# 🚀 Creating the Share Component.mp4
components/PostShare.astro
SVG Code for linkedin/twitter
create PostShare.astro then 
import it and use it in [slug].astro:
```
          <PostShare post={post}/>
```
Here we are passing in the post to the PostShare.astro which uses it here:
```
const {post} = Astro.props
...
href={`https://twitter....nation/blog/${post.slug}`}
```

Source code for the Share component - https://github.com/jamesqquick/astro-course-demo/blob/main/src/components/Share.astro


# 🚀 Intro to Pagination.mp4
Pagination Documentation - https://docs.astro.build/en/core-concepts/routing/#pagination

create [page].astro under blog folder which is next to [slug].astro


# 🚀 Creating The Dynamic Route for Paginated Blog Posts
1 add the Layout tags
2 don't forget the matching imports
3 this is a copy of Layout tags from blog.astro with a minor difference:-
<PostList posts={posts} />
instead of this line:-
<PostList posts={allPosts} />

TEST WITH:-
You should see 6 posts on first page:-
http://localhost:4321/blog/1

You should see 4 posts (10 total -6) on second page:-
http://localhost:4321/blog/2

Original Blog page still gets 10 posts:-
http://localhost:4321/blog/

FINALLY alter original root blog.astro page to mimic [page].astro page 1:
```
// WITHOUT PAGINATION:-
// const allPosts = await getCollection("posts");
// console.log("1 blog.astro")
// console.log(allPosts)

// WITH PAGINATION (this will mimic blog/1 behaviour):-
const sixPosts = (await getCollection("posts")).slice(0,6);
console.log("1 blog.astro 6 posts first page")
console.log(sixPosts)

...
		<div class="mb-32">

			<!-- WITHOUT PAGINATION:- -->
			<!-- <PostList posts={allPosts} /> -->

			<!-- WITH PAGINATION (this will mimic blog/1 behaviour):- -->
			<PostList posts={sixPosts} />

		</div>

```
# 🚀 Creating the Pagination Component.mp4

Create component/Pagination.astro to add PREV and NEXT buttons to paginated pages
this original code had PREV and NEXT buttons overwritting each other:-
```
{
    prevURL && (
      <a 
        href={prevURL} 
        class="bg-teal-900 text-white py-3 px-6 rounded-xl text-xl"
      >
        Previous
      </a>
    )
  }
  {
    nextURL && (
      <a 
        href={nextURL}
        class="bg-teal-900 text-white py-3 px-6 rounded-xl text-xl"
      >
        Next
      </a>
    )
  }
```

So replace && with ternery operators::-