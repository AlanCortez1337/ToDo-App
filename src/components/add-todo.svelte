<script>
    import Info from "./todo-item.svelte";
    
    import { flip } from 'svelte/animate';
    let input;
    let output = [];

    // let removeItem;

    let newInfo = () => {
        let inputObj = {data: input, id: Math.random()};
        output = [...output, inputObj];
    }

    function remove (e) {
        console.log(e.detail);
        output = output.filter((item) => item.id != e.detail);
    }
</script>

<div>
    <input type="text" placeholder="add todo" bind:value={input}>
    <button on:click={newInfo}>send</button>
</div>
<!-- fix -->
{#each output as todo (todo.id)} 
    <div animate:flip="{{duration: 200}}">
        <Info item={todo} on:removeItem={remove} />
    </div>
{/each}

<style>
    div {
        display: flex;
        justify-content: center;
        gap: 10px;
        font-size: 24px;
    }
</style>