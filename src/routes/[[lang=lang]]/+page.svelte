<script lang="ts">
	import Lang from "$lib/Lang.svelte";
	import { languageTag } from "$paraglide/runtime";
	import { LightSwitch } from "@skeletonlabs/skeleton";
	import * as m from "../../paraglide/messages"
</script>
<LightSwitch/>

<p>{m.whattalking()} </p>


<p>{m.pokemon()}</p>

<Lang/>