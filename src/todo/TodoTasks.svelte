<script>
    import TodoTask from './TodoTask.svelte';
    import { tasks } from './store.js';

    let storeTasks;
    const unsubscribe = tasks.subscribe(value => {
		storeTasks = value;
    });
</script>

<div class="tasks">
    {#each storeTasks as task}
        <TodoTask task={task} />
    {/each}
</div>

<style>
    .tasks {
        padding: 10px;
        background-color: #F3F3F3;
    }
</style>
