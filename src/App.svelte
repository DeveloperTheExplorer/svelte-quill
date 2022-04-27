<script lang="ts">
	import { onMount } from 'svelte';

	let editor;

	export let toolbar = [
		[{ header: 1 }, { header: 2 }, "blockquote", "link", "image", "video"],
		["bold", "italic", "underline", "strike"],
		[{ list: "ordered" }, { list: "ordered" }],
		[{ align: [] }],
		["clean"]
	];

	onMount(
		async () => {
			const { default: Quill } = await import('quill');

			let quill = new Quill(editor, {
				modules: {
					toolbar
				},
				theme: 'snow',
				placeholder: 'Welcome pp'
			})
		}
	)
	
	export let name: string;
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>
	<div class="editor-container">
		<div class="editor" bind:this={editor}>
		</div>
	</div>
</main>

<style>
  @import 'https://cdn.quilljs.com/1.3.6/quill.snow.css';
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>