<script>
	import GitHubButton from './GitHubButton.svelte';
	import GitHubButton2 from './GitHubButton copy.svelte';
</script>

<div
	class="max-w-4xl mx-auto w-full flex md:flex-row flex-col items-center md:justify-between py-8 mt-20 border-t border-white/20"
>
	<div class="text-white/70 flex items-center flex-none">
		Powered by <span class="mx-1 font-bold"> OpenAI</span>
		and
		<span class="ml-1 font-bold">Vercel Edge Functions</span>.
	</div>
	<div class="flex items-center mt-2 md:mt-0 space-x-2">
		<GitHubButton2 />
		<GitHubButton />
	</div>
</div>
