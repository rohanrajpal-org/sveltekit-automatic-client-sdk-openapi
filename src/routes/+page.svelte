<script lang="ts">
  import { GET } from '$lib/api';
</script>

<h1>Welcome to SvelteKit</h1>
<p>
  Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation
</p>
<h1>Test</h1>
{#await GET( '/pet/findByStatus', { params: { query: { status: 'available' } } }, )}
  <p>...waiting</p>
{:then { data }}
  {#if data}
    {#each data as pet}
      <div class="pet">
        <p>{pet.name}</p>
        <br />
        <p>{pet.id}</p>
      </div>
    {/each}
  {/if}
{/await}

<style>
  h1 {
    font-family: Arial, sans-serif;
  }

  p {
    color: #333; /* Dark grey */
    font-family: 'Times New Roman', Times, serif;
  }

  .pet {
    border: 1px solid #ddd;
    border-radius: 8px;
    padding: 10px;
    margin: 10px 0;
    max-width: 200px;
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: #f9f9f9;
  }

  .pet p {
    margin: 5px 0;
  }
</style>
