<script lang="ts">
    import GalleryCard from "$lib/components/GalleryCard.svelte";
    import { artworks } from "$lib/index";
    import Header from "$lib/components/Header.svelte";
</script>

<Header />
<div class="mx-auto max-w-7xl px-8">
    <div class="mt-6 grid grid-cols-4 justify-items-center gap-x-10 gap-y-14">
        {#each artworks as artwork}
            <a href="/g/{artwork.id}">
                <GalleryCard {artwork} />
            </a>
        {/each}
    </div>
</div>
