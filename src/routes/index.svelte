
<script>
    import Monaco from "$lib/Monaco.svelte";
    let editors=new Array(12);
    let dirty = false;
    
    function handleChanged(){
        dirty = true;
    }
    function handleSave(){
        for(let i=0;i<12;++i){
            editors[i].save();
        }

        dirty = false;
    }
</script>
<h1>Welcome to SvelteKit</h1>
{#if dirty}
<div class="savebutton"><button class='button-7' on:click={handleSave}>Save</button></div>
{/if}
<Monaco bind:this={editors[0]} text="SELECT * FROM TABLE1" on:changed={handleChanged}></Monaco>
<Monaco bind:this={editors[1]}  on:changed={handleChanged}></Monaco>
<Monaco bind:this={editors[2]}  on:changed={handleChanged}></Monaco>
<Monaco bind:this={editors[3]}  on:changed={handleChanged}></Monaco>
<Monaco bind:this={editors[4]}  on:changed={handleChanged}></Monaco>
<Monaco bind:this={editors[5]}  on:changed={handleChanged}></Monaco>
<Monaco bind:this={editors[6]}  on:changed={handleChanged}></Monaco>
<Monaco bind:this={editors[7]}  on:changed={handleChanged}></Monaco>
<Monaco bind:this={editors[8]}  on:changed={handleChanged}></Monaco>
<Monaco bind:this={editors[9]}  on:changed={handleChanged}></Monaco>
<Monaco bind:this={editors[10]}  on:changed={handleChanged}></Monaco>
<Monaco bind:this={editors[11]}  on:changed={handleChanged}></Monaco>

<p><a href="https://github.com/microsoft/sqltoolsservice">Language service link</a></p>
<p><a href="https://github.com/microsoft/vscode-mssql">VSCode add-in</a></p>
<style>
    .savebutton{
       
       width:100%;
       text-align:right;
       padding: 16px;
    }
  


/* CSS */
.button-7 {
  background-color: #0095ff;
  border: 1px solid transparent;
  border-radius: 3px;
  box-shadow: rgba(255, 255, 255, .4) 0 1px 0 0 inset;
  box-sizing: border-box;
  color: #fff;
  cursor: pointer;
  display: inline-block;
  font-family: -apple-system,system-ui,"Segoe UI","Liberation Sans",sans-serif;
  font-size: 13px;
  font-weight: 400;
  line-height: 1.15385;
  margin: 0;
  outline: none;
  padding: 8px .8em;
  position: relative;
  text-align: center;
  text-decoration: none;
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  vertical-align: baseline;
  white-space: nowrap;
}

.button-7:hover,
.button-7:focus {
  background-color: #07c;
}

.button-7:focus {
  box-shadow: 0 0 0 4px rgba(0, 149, 255, .15);
}

.button-7:active {
  background-color: #0064bd;
  box-shadow: none;
}
</style>