<script lang="ts">
	import { onDestroy, onMount } from 'svelte';
	//import { fade } from 'svelte/transition';

	import { flyAndScale } from '$lib/utils/transitions';

	export let show = true;
	export let size = 'md';
	//export let containerClassName = 'p-3';
	export let className = 'bg-white dark:bg-gray-900 rounded-2xl';

	//let modalElement = null;
	//let mounted = false;

	const sizeToWidth = (size) => {
		if (size === 'full') {
			return 'w-full';
		}		
	};

	const handleKeyDown = (event: KeyboardEvent) => {
	
	};


	onDestroy(() => {
		window.removeEventListener('keydown', handleKeyDown);  
		
	});
</script>

{#if show}	
	<div  class="embedded-modal relative my-6 mx-auto {sizeToWidth(size)}" 
	     transition:flyAndScale>
		<div class="m-auto max-w-full shadow-3xl min-h-fit scrollbar-hidden 
		  in:flyAndScale ">
			<slot />
		</div>
	</div>
{/if}

<style>
	/* 🔄 替换为内嵌动画 */
	.embedded-modal {
	  animation: embedFadeIn 0.2s ease-out;
	}
	@keyframes embedFadeIn {
	  from { opacity: 0; transform: translateY(8px); }
	  to { opacity: 1; transform: translateY(0); }
	}
</style>