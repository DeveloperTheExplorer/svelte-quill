<style lang="scss" global>
  @import './main.sass';
</style>

<script lang="ts">
	import { onMount } from 'svelte';
	import EditorToolbar from '@/components/EditorToolbar/index.svelte';

	let editor;

	onMount(
		async () => {
			const { default: Quill } = await import('quill');

			let quill = new Quill(editor, {
				modules: {
					toolbar: '#toolbar'
				},
				theme: 'snow',
				placeholder: 'Here is the truth...'
			})
		}
	)
</script>

<div class="editor-container">
	<EditorToolbar />
	<input id="title" type="text" class="text-3xl" placeholder="The story of...">
	<div class="editor" bind:this={editor}></div>
</div>
