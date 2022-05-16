<script lang="ts">
	export let name: string;

	let src = './progress.png'

	let user1 = {keepProcess : true};
	let user2 = {holdProcess : true};

	function keepLoading(){
		user1.keepProcess = !user1.keepProcess;
	}

	function holdLoading(){
		user2.holdProcess = !user2.holdProcess;
	}

</script>

<main class="text-center p-1 max-w-xs m-auto">

	<div>
		{#if user1.keepProcess}
		<button on:click={keepLoading} >Keep Process</button>
		{:else}
		<button on:click={keepLoading}>Loading...</button>
		<img {src} alt={name} class="animate-rotated w-14 fixed right-14 bottom-14">
		{/if}
	</div>

	<br/>

	<div>
		{#if user2.holdProcess}
		<button on:click={holdLoading}>Hold Process</button>
		{:else}
			<button on:click={holdLoading} class="z-50 relative bg-white"> reset</button>
			<div class="fixed top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2">
				<img {src} alt={name} class="w-14 animate-rotated opacity-80">
			</div>
			<div class="w-full h-full left-0 top-0 fixed bg-gray-500/30"></div>
			
		{/if}
	</div>
	

</main>

<style lang="postcss">

	@tailwind base;
	@tailwind components;
	@tailwind utilities;

</style>