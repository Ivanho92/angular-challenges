<script>
  import { onMount } from 'svelte';


  let sponsors = [];

  onMount(async () => {
    const sponsorFetch = await fetch('https://ghs.vercel.app/v2/sponsors/tomalaforge');
    const data = await sponsorFetch.json();
    sponsors = data.sponsors.past;
  });

</script>

{#each sponsors as { username, avatar }}
  <a href={`https://github.com/${username}`}>
    <img
      loading="lazy"
      src={avatar}
      width="40"
      height="40"
      alt={username}
      class="avatar"
    />
  </a>
{/each}

<style>
  .avatar {
    border-radius: 50%;
    width: 30px;
    height: auto;
    vertical-align: middle;
    margin-right: 0.5rem;
  }
</style>
