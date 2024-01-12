<script lang="ts">
	import '../app.postcss';
	import { AppShell, AppBar } from '@skeletonlabs/skeleton';

	// Highlight JS
	import hljs from 'highlight.js/lib/core';
	import 'highlight.js/styles/github-dark.css';
	import { storeHighlightJs } from '@skeletonlabs/skeleton';
	import xml from 'highlight.js/lib/languages/xml'; // for HTML
	import css from 'highlight.js/lib/languages/css';
	import javascript from 'highlight.js/lib/languages/javascript';
	import typescript from 'highlight.js/lib/languages/typescript';
//Free Icon
	import '@fortawesome/fontawesome-free/css/fontawesome.css';
	import '@fortawesome/fontawesome-free/css/brands.css';
	import '@fortawesome/fontawesome-free/css/solid.css';
	hljs.registerLanguage('xml', xml); // for HTML
	hljs.registerLanguage('css', css);
	hljs.registerLanguage('javascript', javascript);
	hljs.registerLanguage('typescript', typescript);
	storeHighlightJs.set(hljs);

	// Floating UI for Popups
	import { computePosition, autoUpdate, flip, shift, offset, arrow } from '@floating-ui/dom';
	import { storePopup } from '@skeletonlabs/skeleton';
	storePopup.set({ computePosition, autoUpdate, flip, shift, offset, arrow });

	//InLang
	import { page } from "$app/stores";
  import { setLanguageTag, sourceLanguageTag, type AvailableLanguageTag } from "$paraglide/runtime";
  import { getTextDirection } from "$lib/i18n.js"
	import { browser } from '$app/environment';
  //Use the default language if no language is given
  $: lang = $page.params.lang as AvailableLanguageTag ?? sourceLanguageTag;
  $: setLanguageTag(lang);

	//Determine the text direction of the current language
	$: textDirection = getTextDirection(lang)

	//Keep the <html> lang and dir attributes in sync with the current language
	$: if (browser) {
		document.documentElement.dir = textDirection
		document.documentElement.lang = lang
	}
</script>

<!-- App Shell -->
<AppShell>
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar>
			<svelte:fragment slot="lead">
				<strong class="text-xl uppercase">Skeleton</strong>
			</svelte:fragment>
		
		</AppBar>
	</svelte:fragment>
	{#key lang}
	<slot></slot>
  {/key}
</AppShell>
