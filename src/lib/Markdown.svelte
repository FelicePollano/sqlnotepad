<script>
    import SvelteMarkdown from 'svelte-markdown'
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();
    export let source;
    export const save=()=>{
        editing=false;
    }
    let editing=true;
  
    function handleChanged(){
        dispatch('changed');
    }
    function enterEdit(){
        editing=!editing;
    }
   
</script>
{#if editing}
<div class="editorcontainer" >
<textarea width=100% bind:value={source}  on:input={handleChanged}></textarea>
</div>
{/if}
<div class="markdowncontainer" on:click={enterEdit}>
<SvelteMarkdown on:click={enterEdit} {source}></SvelteMarkdown>
</div>




<style>
    textarea{
        width:100%;
        height: 200px;
    }
</style>