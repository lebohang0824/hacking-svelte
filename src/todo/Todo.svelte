<script>
    import TodoHeader from './TodoHeader.svelte';
    import TodoTasks from './TodoTasks.svelte';

    let tasks = [];

    const addTaskHandler = e => {
        const task = {
            id: tasks.length++,
            title: e.target[0].value 
        }

        let newTasks = tasks.filter(n => n !== null);
        newTasks.unshift(task);

        tasks = newTasks;
        e.target[0].value = null;
    }
</script>

<div class="todo">
    <TodoHeader on:submit={addTaskHandler} />
    <TodoTasks tasks={tasks} />
</div>

<style>
    .todo {
        width: 500px;
        margin: 5% auto;
    }
</style>