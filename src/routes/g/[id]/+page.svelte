<script lang="ts">
    import Header from "$lib/components/Header.svelte";
    import { page } from "$app/state";
    import { artworks } from "$lib/index";

    const artwork = artworks.find((a) => a.id === Number(page.params.id));
</script>

<Header />

<div
    class="mx-auto grid max-w-7xl items-start gap-8 px-4 py-6 md:grid-cols-[180px_auto] md:justify-center md:gap-16 md:px-16"
>
    <div
        class="contents md:col-start-1 md:row-start-1 md:flex md:flex-col md:items-center md:justify-start md:self-stretch md:pt-8"
    >
        <a
            href="/"
            class="group order-1 inline-flex w-44 -rotate-2 items-center gap-2 justify-self-start whitespace-nowrap bg-[#FAF9F6] px-4 py-2 font-mono text-sm font-bold uppercase tracking-wide text-black shadow-md transition hover:rotate-0 hover:bg-white hover:shadow-xl focus-visible:outline-2 focus-visible:outline-offset-4 focus-visible:outline-[#FAF9F6]"
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
            class="order-3 mt-6 w-44 rotate-2 bg-[#FAF9F6] p-4 shadow-xl transition duration-300 hover:rotate-0"
        >
            <p class="font-sans text-xl text-black">Artist:</p>
            <p class="font-sans text-xl text-black">@{artwork?.artist}</p>
        </div>
    </div>

    <div class="order-2 flex justify-center md:col-start-2 md:row-start-1">
        <div class="bg-[#FAF9F6] p-4 pt-6 pb-15 shadow-xl">
            <img
                src={artwork?.image}
                alt={artwork?.artist}
                class="max-h-[calc(100dvh-16rem)] max-w-full object-contain md:max-h-[calc(100dvh-10rem)]"
            />
        </div>
    </div>
</div>
