<script lang="ts">
    import GalleryCard from "$lib/components/GalleryCard.svelte";
    import { artworks} from "$lib/index";
    import Header from "$lib/components/Header.svelte"
</script>

<div class="mx-auto max-w-7xl px-8 py-10">
    <Header title="asagi@gallery" />

	<div class="mt-14 grid grid-cols-4 justify-items-center gap-x-10 gap-y-14">
		{#each artworks as artwork}
			<GalleryCard artwork={artwork} />
		{/each}
	</div>
</div>