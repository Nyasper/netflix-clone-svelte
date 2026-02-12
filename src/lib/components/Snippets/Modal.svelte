<script lang="ts" module>
  import type { getModalContext } from '$lib/stores/ModalStore.svelte';
  type modalContextType = ReturnType<typeof getModalContext>;

  export { genres, spokenLanguages };
</script>

{#snippet genres(modalContext: modalContextType)}
  <div class="flex lg:ml-40">
    {#if Array.isArray(modalContext?.movieData?.genres) && modalContext.movieData.genres.length > 0}
      <span class="font-semibold">Genre:&nbsp;</span>
      {#each modalContext.movieData.genres.slice(0, 3) as genre (genre.id)}
        <span class="mr-2">{genre.name}</span>
      {/each}
    {:else}
      <span class="font-semibold">Genre: N/A</span>
    {/if}
  </div>
{/snippet}

{#snippet spokenLanguages(modalContext: modalContextType)}
  <div class="mt-2 flex lg:ml-40">
    <span class="font-semibold">Available in: &nbsp;</span>
    {#if Array.isArray(modalContext?.movieData?.spoken_languages) && modalContext.movieData.spoken_languages.length > 0}
      {#each modalContext.movieData.spoken_languages as lang (lang.iso_639_1)}
        <span class="mr-2">{lang.name}</span>
      {/each}
    {:else}
      <span class="font-semibold">N/A</span>
    {/if}
  </div>
{/snippet}
