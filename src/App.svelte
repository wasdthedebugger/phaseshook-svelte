<script>
  import { onMount, afterUpdate } from "svelte";
  import Feed from "./Feed.svelte";
  import Footer from "./Footer.svelte";
  import Nav from "./Nav.svelte";
  import Sidebar from "./Sidebar.svelte";

  let feeds = [];
  let loading = false;
  let scrollContainer;

  async function fetchMemes() {
    try {
      loading = true;
      let memesFetched = 0;
      while (memesFetched < 10) {
        const response = await fetch(
          "https://www.reddit.com/r/memes/random.json"
        );
        const data = await response.json();
        const meme = data[0]?.data?.children?.[0];
        if (meme) {
          const imageUrl = meme.data.url_overridden_by_dest;
          feeds = [...feeds, { imageUrl }];
          memesFetched++;
        }
      }
    } catch (error) {
      console.error("Failed to fetch memes:", error);
    } finally {
      loading = false;
    }
  }

  onMount(fetchMemes);

  function loadMore() {
    fetchMemes();
  }

  afterUpdate(() => {
    if (scrollContainer) {
      // Scroll to the bottom of the feed only when new memes are added and not when updating
      const { scrollTop, scrollHeight, clientHeight } = scrollContainer;
      const atBottom = scrollTop + clientHeight === scrollHeight;
      if (atBottom) {
        scrollContainer.scrollTop = scrollContainer.scrollHeight;
      }
    }
  });
</script>

<Nav />
<br />
<div class="main">
  <Sidebar />
  <div class="scroll" bind:this={scrollContainer}>
    {#each feeds as feed}
      <Feed imageUrl={feed.imageUrl} />
    {/each}
    {#if loading}
      <div class="loading">Loading</div>
    {:else if feeds.length >= 10}
      <button on:click={loadMore}>See More</button>
    {/if}
  </div>
</div>
<br />
<Footer />

<style>
  .main {
    width: 60%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: auto;
    gap: 20px;
  }

  .scroll {
    height: 100vh;
    overflow-y: scroll;
    width: 60%;
    display: flex;
    align-items: center;
    flex-direction: column;
    background-color: #333;
  }

  /* don't show scroll bar of scroll */
  .scroll::-webkit-scrollbar {
    display: none;
  }

  .scroll button {
    width: 100%;
    height: 100%;
    border: none;
    padding: 10px;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    padding: 10px;
  }

  .loading{
    width: 100%;
    height: 50px;
    border: none;
    padding: 10px;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    padding: 10px;
    color: #fff;
    text-align: center;
    background-color: #aea7a7d1;
  }

  /* show the sidebar at top on small screens */
  @media screen and (max-width: 800px) {
    .main {
      flex-direction: column;
      width: 100%;
    }
    .scroll {
      width: 100%;
    }
  }
</style>
