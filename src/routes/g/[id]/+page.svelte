<script lang="ts">
    import Header from "$lib/components/Header.svelte"
    import { page } from "$app/state"
    import { artworks } from "$lib/index";

    const artwork = artworks.find(
        (a) => a.id === Number(page.params.id)
    )
</script>

<Header title="*****@gallery" />

<div class="mx-auto grid max-w-7xl grid-cols-[180px_1fr] items-start gap-16 px-16 py-8">
	<div class="bg-white p-4 shadow-xl">
		<p class="text-xl text-black font-mono">Artist:</p>
		<p class="text-xl text-black font-mono">@{artwork?.artist}</p>
	</div>

	<div class="flex justify-center">
		<div class="bg-white p-4 pt-6 pb-15 shadow-xl">
			<img
				src={artwork?.image}
				alt={artwork?.artist}
				class="w-full object-cover"
			/>
		</div>
	</div>
</div>