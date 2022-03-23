<script>
    import Todo from "../components/add-todo.svelte"
    // import NewItem from "../components/todo-item.svelte"

    let items = [];


</script>

<h1>To-do List</h1>
<Todo/>
<!-- <NewItem item="sure"/> -->
<style>
    h1 {
        display: flex;
        justify-content: center;
        font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    }
</style>