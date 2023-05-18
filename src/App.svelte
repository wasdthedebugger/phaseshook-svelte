<script>
  import Feed from "./Feed.svelte";
  import Footer from "./Footer.svelte";
  import Nav from "./Nav.svelte";
  import Sidebar from "./Sidebar.svelte";
</script>

<Nav />
<br />
<div class="main">
  <Sidebar />
  <div class="scroll">
    <Feed />
    <Feed />
    <Feed />
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

  /* dont show scroll bar of scroll */
  .scroll::-webkit-scrollbar {
    display: none;
  }

  /* show the sidebar at top in small screens*/
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
