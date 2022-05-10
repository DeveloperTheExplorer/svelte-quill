<script lang="ts">
    export let quill;

    let editorBounds;
    let toolbarBounds = {
        top: 0,
        left: 0,
        display: 'none'
    };

    const updateXY = (_: Event) => {
        const editor = document.querySelector('#editor');
        editorBounds = editor.getBoundingClientRect();
    }
    
    window.addEventListener('resize', updateXY);
    window.onload = updateXY;

    const initQuillListeners = (q) => {
        if (!q) {
            return;
        }

        q.on('selection-change', (e) => {
            if (e.length === 0) {
                toolbarBounds.display = 'none';
                
                return;
            }

            const { left, top, width } = q.getBounds(e.index, e.length);

            toolbarBounds = {
                top: top + editorBounds.top - 48,
                left: left + editorBounds.left + (width / 2),
                display: 'flex'
            }
        })
    }


	$: initQuillListeners(quill);
</script>

<div 
    id="popup-toolbar"
    class="toolbar"
    style:display="{toolbarBounds.display}"
    style:top="{toolbarBounds.top}px"
    style:left="{toolbarBounds.left}px"
>
    <button class="editor-button ql-header ql-size ql-active" value={3}>
        H1
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

<div id='toolbar' class="toolbar">
    <button class="editor-button ql-header ql-size ql-active" value={3}>
        H1
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

<style type='text/sass' global>
    @import './main.sass'
</style>