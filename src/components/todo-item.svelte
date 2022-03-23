<script>
    import { createEventDispatcher } from 'svelte';
    import { fly } from 'svelte/transition';


    export let item; //{data: something, id: #}
    export let done = false;
    let out = false;
    
    let dispatch = createEventDispatcher();
    


    const handleDispatch = () => {
        out = true;
        dispatch('removeItem', item.id);
    }

    const markDone = () => {
        if(done === false) {
            done = true;
        } else {
            done = false;
        }
    }
</script>
<div>
    <div in:fly={{x:200, duration: 200}} out:fly={{x:-200, duration: 200}} class="newitem">
        <div class="{done === true ? 'donezo' : ''} card">
            <!-- <div class="card-wrapper"> -->
                <ul><li>{item.data}</li></ul>
                <div class="buttons">
                    <button on:click={markDone}>✅</button>
                    <button on:click={handleDispatch}>❌</button>
                </div>
            <!-- </div> -->
        </div>
    </div>
</div>
<style>
    .newitem {
        display: flex;
        justify-content: center;
        padding: 15px;
    }
    .card {
        display: flex;
        justify-content: space-between;
        align-items: center;
        background-color: white;
        color: black;
        border: black 1px solid;
        border-radius: 20px;
        min-width: 200px;
        height: 50px;
        gap: 10px;
        padding: 5px 15px 5px 5px;
        font-size: 24px;
    }

    button {
        border: none;
        background-color: inherit;
        font-size: 18px;
    }


    .donezo {
        /* background-color: red; */
        /* text-decoration: line-through; */
        opacity: 0.25;
    }
</style>