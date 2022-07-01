
<script>

import { createEventDispatcher } from 'svelte';

const dispatch = createEventDispatcher();


export let text;
export let markup;
export const save=()=>{
    markup = div.innerHTML;
    console.log(markup);
}
let div;
let editor;
async function loadMonaco(){
    if(!editor){
    let monaco=await import('monaco-editor');    
    editor = monaco.editor.create(div, {
            value: text,
            language: 'sql',
            minimap: { enabled: false },
                automaticLayout: true,
                scrollBeyondLastLine: false
        });
        recalcHeight(editor,div);
        editor.getModel().onDidChangeContent((event) => {
                    recalcHeight(editor,div);
                    dispatch('changed');
                
                });
        }
    }

    let recalcHeight=(editor,div)=>{
    const contentHeight = editor.getModel().getLineCount() * 19 ;
    div.style.height=32+contentHeight+'px';
    editor.layout();
}
</script>
<div on:click={loadMonaco} class="monacocontainer" bind:this={div}>
    
</div>
<style>
    .monacocontainer{
        margin-top:-1px;
        border:1px dashed rgb(180,180,180);
        text-align: left;
        min-height: 20px;
    }
</style>