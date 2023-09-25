<!-- This get's shipped with the template -- don't do local imports from $lib -->

<script>
	import '../app.css';
	import { navigating } from '$app/stores';
	import { blur } from 'svelte/transition';
	import { page } from '$app/stores';
	import { dev } from '$app/environment';

	let open = false;
	//TODO: Offer this as a build parameter
	// in dev. mode prevent prefetch on "hover"
	const prefetchStrategy = dev ? 'tap' : 'hover';
</script>

<!-- eslint-disable no-undef -->

{#if $navigating}
	<LoadingIndicator />
{/if}


	{#if !$navigating}
		<main in:blur|local id="evidence-content">
			<div class="content" class:settings-content={$page.url.pathname.startsWith('/settings')}>
				<article class:settings-article={$page.url.pathname.startsWith('/settings')} class="justify-center" >
					<slot />
					<p>&nbsp;</p>
				</article>
			</div>
		</main>
	{/if}
{#if !$navigating && dev && !$page.url.pathname.startsWith('/settings')}
	<QueryStatus />
{/if}

<div class="flex justify-center fixed bottom-0 mx-auto bg-white w-full">
	<div class="justify-self-center">Powered by </div>
	<div class="mt-1 ml-2"><img alt=Evidence class="h-5" src=https://raw.githubusercontent.com/evidence-dev/media-kit/main/png/wordmark-gray-800.png /></div>
</div>

<style>

	div.content {
		margin: auto;
		box-sizing: border-box;
		justify-items: left;
	}

	article {
		padding: 0 1.5em 0 1.5em;
		box-sizing: border-box;
		user-select: text;
		-moz-user-select: text;
		-webkit-user-select: text;
		-ms-user-select: text;
	}

	.settings-content {
		max-width: 100ch !important;
		grid-template-columns: 1fr !important;
		grid-template-areas: 'article' !important;
	}

	.settings-article {
		max-width: 100ch;
		min-width: 0;
		width: 100%;
		grid-area: article;
		padding: 0 1.5em 0 1.5em;
		box-sizing: border-box;
	}


	@media print {
		main * {
			visibility: hidden;
		}
		article,
		article * {
			visibility: visible;
		}
		article {
			position: absolute;
			left: 0;
			top: 0;
		}
	}
</style>
