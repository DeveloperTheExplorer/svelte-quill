<style type='text/sass' global>
	@import './main.sass'
</style>

<script lang="ts">
    import FaFont from 'svelte-icons/fa/FaFont.svelte'

</script>

<div id="toolbar">
    <button class="editor-button ql-header ql-size large ql-active" value={1}>
        T
    </button>
    <button class="editor-button ql-size small" value="">
        T
    </button>

    <span class="divider"></span>
    
    <button class="editor-button ql-bold"></button>
    <button class="editor-button ql-italic"></button>
    <button class="editor-button ql-underline"></button>
    
    <span class="divider"></span>

    <button class="editor-button ql-align ql-active" value=""></button>
    <button class="editor-button ql-align" value="center"></button>
    <button class="editor-button ql-align" value="right"></button>
    <button class="editor-button ql-align" value="justify"></button>
</div>