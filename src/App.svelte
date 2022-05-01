<style global lang="scss">
	@import './styles/main.sass';
	@tailwind base;
	@tailwind components;
	@tailwind utilities;
</style>

<script lang="ts">
	import Editor from '@/components/Editor/index.svelte'

</script>

<main class="container mx-auto py-10">
	<h1 class="text-3xl font-semibold">Hello dude!</h1>

	<Editor />
</main>
