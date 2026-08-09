<script lang="ts">
    let { artwork } = $props<{
        artwork: {
            id: number;
            artist: string;
            image: string;
            preview: string;
        };
    }>();
</script>

<div
    class="w-full max-w-[15rem] rotate-[-2deg] bg-[#FAF9F6] p-2 pb-10 pt-3 shadow-xl transition duration-300 hover:rotate-0 hover:scale-105 active:rotate-0 active:scale-105 sm:max-w-[15rem] sm:p-4 sm:pb-15 sm:pt-6 md:w-72 md:max-w-none"
>
    <img
        src={artwork.preview}
        alt={artwork.artist}
        class="aspect-square w-full object-cover"
    />
</div>
