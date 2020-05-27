<script>
    import TodoHeader from './TodoHeader.svelte';
    import TodoTasks from './TodoTasks.svelte';
</script>

<div class="todo">
    <TodoHeader />
    <TodoTasks />
</div>

<style>
    .todo {
        width: 500px;
        margin: 5% auto;
    }
    @media screen and (max-width: 510px) {
        .todo {
            width: 100%;
            padding: 5px;
            box-sizing: border-box;
        }
    }
</style>