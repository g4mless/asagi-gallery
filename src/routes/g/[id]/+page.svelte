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
        <a
            href="/"
            class="group mb-6 inline-flex -rotate-2 items-center gap-2 bg-[#FAF9F6] px-4 py-2 font-mono text-sm font-bold uppercase tracking-wide text-black shadow-md transition hover:rotate-0 hover:bg-white hover:shadow-xl focus-visible:outline-2 focus-visible:outline-offset-4 focus-visible:outline-[#FAF9F6]"
            aria-label="Back to gallery"
        >
            <svg
                aria-hidden="true"
                viewBox="0 0 20 20"
                fill="none"
                class="h-4 w-4 transition-transform group-hover:-translate-x-1"
            >
                <path
                    d="M15.5 10H4.5m0 0 4 4m-4-4 4-4"
                    stroke="currentColor"
                    stroke-width="1.8"
                    stroke-linecap="round"
                    stroke-linejoin="round"
                />
            </svg>
            Back to gallery
        </a>
        <div
            class="rotate-2 bg-[#FAF9F6] p-4 shadow-xl transition duration-300 hover:rotate-0"
        >
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
