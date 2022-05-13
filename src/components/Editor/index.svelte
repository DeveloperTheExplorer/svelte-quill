<style lang="scss" global>
  @import './main.sass';
</style>

<script lang="ts">
	import { onMount } from 'svelte';
	import EditorToolbar from '@/components/EditorToolbar/index.svelte';
	
	let editor;
	let quill;

	onMount(
		async () => {
			const { default: Quill } = await import('quill');

			quill = new Quill(editor, {
				modules: {
					toolbar: '#toolbar'
				},
				theme: 'snow',
				placeholder: 'Here is the truth...'
			})
		}
	);
</script>

<div class="editor-container">
	<EditorToolbar quill={quill} />
	<input id="title" type="text" class="text-3xl" placeholder="The story of...">
	<div id="editor" class="editor" bind:this={editor}></div>
</div>
