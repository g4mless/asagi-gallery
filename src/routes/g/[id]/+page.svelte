<script lang="ts">
    import Header from "$lib/components/Header.svelte";
    import { page } from "$app/state";
    import { artworks } from "$lib/index";

    const artwork = artworks.find((a) => a.id === Number(page.params.id));
</script>

<Header />

<div
    class="mx-auto grid max-w-7xl grid-cols-[180px_1fr] items-start gap-16 px-16 py-6"
>
    <div>
        <a href="/" class="text-2xl">back</a>
        <div class="bg-[#FAF9F6] p-4 shadow-xl">
            <p class="text-xl text-black font-sans">Artist:</p>
            <p class="text-xl text-black font-sans">@{artwork?.artist}</p>
        </div>
    </div>

    <div class="flex justify-center">
        <div class="bg-[#FAF9F6] p-4 pt-6 pb-15 shadow-xl">
            <img
                src={artwork?.image}
                alt={artwork?.artist}
                class="w-full object-cover"
            />
        </div>
    </div>
</div>
