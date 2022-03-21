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
import { stringify } from "postcss";

  export let posts = []
</script>


<!-- This line of code below is to show posts in Json format in the browser -->
<!-- <pre>{JSON.stringify(posts, null, 2)}</pre> --> 

<h1>Welcome to SvelteKit</h1>
<p>
  Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the
  documentation
</p>
