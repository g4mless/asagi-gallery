<script lang="ts">
    let { artwork } = $props<{
        artwork: {
            artist: string
            image: string
        }
    }>()
</script>

<div class="w-72 rotate-[-2deg] bg-white p-4 shadow-xl transition duration-300 hover:rotate-0 hover:scale-105 pb-15 pt-6">
	<img
		src={artwork.image}
		alt={artwork.artist}
		class="aspect-square w-full object-cover"
	/>
</div>