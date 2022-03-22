<script context="module">
export const load = async ({fetch}) => {
  const res = await fetch('/posts.json');
  if (res.ok) {
    const {posts} = await res.json()
    return  {
      props: {posts},
    }
  }
}
</script>

<script>
// import { stringify } from "postcss";
  export let posts 
</script>
<!-- This line of code below is to show posts in Jclearson format in the browser -->
<!-- <pre>{JSON.stringify(posts, null, 2)}</pre>  -->

<svelte:head>
  <title>Creative Lightbox</title>
</svelte:head>

<h1 class="text-4xl mb10 font-extrabold">Welcome to Creative Lightbox</h1>

<!-- <p>
  Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the
  documentation
</p> -->

{#each posts as {title, slug, excerpt, coverImage, tags}}
  <div class="card text-center shadow-2xl mb-20">
    <figure class="px-10 pt-10">
      <img 
      class="rounded-xl" 
      src={coverImage.url} 
      alt={`Cover image for ${title}`}
      />
    </figure>

    <div class="card-body">
      <h2 class="title">{title}</h2>
      <!-- <p class="excerpt">{excerpt}</p> -->
      <p>{excerpt}</p>
      <div class="flex justify-center mt-5 space-x-2">
      {#each tags as tag}
      <span class="badge badge-primary">{tag}</span>
      {/each}
    </div>
    <div class="justify-center card-actions">
      <a href={`/posts/${slug}`} class="btn btn-outline btn-primary">Read More &rArr;</a>
    </div>
  </div>
  </div>
{/each}