<script lang="ts">
    let { title } = $props<{
        title: string
    }>()
</script>

<header class="bg-[#001D4C]">
	<div class="mx-auto max-w-7xl px-8 py-5">
		<h1 class="font-mono text-5xl font-bold text-white">
			&gt; {title}
		</h1>
	</div>
</header>