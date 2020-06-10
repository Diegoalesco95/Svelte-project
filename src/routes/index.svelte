<script context="module">
  export async function preload() {
    let data = {};
    const response = await this.fetch(
      `https://us-central1-pugstagram-co.cloudfunctions.net/data`
    );
    data = await response.json();
    return { data };
  }
</script>

<script>
  import Main from "../components/Main.svelte";
  import SideBar from "../components/SideBar.svelte";
  import TimeLine from "../components/TimeLine.svelte";
  export let data;
</script>

<svelte:head>
  <title>Pugstagram</title>
</svelte:head>

<Main>
  <TimeLine posts={data.posts} />
  <SideBar {...data.user} />
</Main>
