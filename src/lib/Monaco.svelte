
<script>

import { onMount } from 'svelte';
export let text;
let div;
onMount( async ()=>{
let monaco=await import('monaco-editor');    
let editor = monaco.editor.create(div, {
        value: text,
        language: 'sql',
        minimap: { enabled: false },
            automaticLayout: true,
            scrollBeyondLastLine: false
    });
    const contentHeight = editor.getModel().getLineCount() * 19 ;
    
    div.style.height=32+contentHeight+'px';
    editor.layout();
    editor.getModel().onDidChangeContent((event) => {
                const contentHeight = editor.getModel().getLineCount() * 19 ;
                div.style.height=32+contentHeight+'px';
                editor.layout();
            });
});
</script>
<div class="monacocontainer" bind:this={div}>
    
</div>
<style>
    .monacocontainer{
        margin-top:-1px;
        border:1px dashed rgb(180,180,180);
        text-align: left;
    }
</style>