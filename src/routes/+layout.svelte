<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';
	import { onNavigate, goto } from '$app/navigation';
	import "../app.css";

	let { children } = $props();

	async function waitForImages(timeoutMs = 4000): Promise<void> {
		const imgs = Array.from(document.querySelectorAll('img')) as HTMLImageElement[];
		if (imgs.length === 0) return;
		const withTimeout = <T>(p: Promise<T>): Promise<T | void> =>
			Promise.race([p, new Promise<void>((r) => setTimeout(r, timeoutMs))]);
		await withTimeout(
			Promise.all(
				imgs.map(async (img) => {
					if (!img.complete) {
						await new Promise<void>((resolve) => {
							img.addEventListener('load', () => resolve(), { once: true });
							img.addEventListener('error', () => resolve(), { once: true });
						});
					}
					try { await img.decode(); } catch { /* ignore broken decode */ }
				})
			)
		);
	}

	onNavigate((navigation) => {
		// @ts-ignore - View Transition API not yet in lib.dom
		if (!document.startViewTransition) return;
		return new Promise((resolve) => {
			// @ts-ignore
			document.startViewTransition(async () => {
				resolve();
				await navigation.complete;
				await Promise.all([
					document.fonts?.ready.catch(() => {}) ?? Promise.resolve(),
					waitForImages()
				]);
			});
		});
	});

	function onKeydown(e: KeyboardEvent) {
		if (e.key.toLowerCase() !== 'g') return;
		const t = e.target as HTMLElement | null;
		if (t && (t.tagName === 'INPUT' || t.tagName === 'TEXTAREA' || t.isContentEditable)) return;
		if (e.ctrlKey || e.metaKey || e.altKey) return;
		e.preventDefault();
		const path = location.pathname;
		if (path.startsWith('/g/')) goto('/');
		else if (path === '/') goto('/g/1');
		else goto('/');
	}
</script>

<svelte:window onkeydown={onKeydown} />

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children()}
