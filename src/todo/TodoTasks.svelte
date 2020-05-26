<script>
    import TodoTask from './TodoTask.svelte';

    export let tasks;
</script>

<div class="tasks">
    {#each tasks as task}
        <TodoTask task={task} />
    {/each}
</div>

<style>
    .tasks {
        padding: 10px;
        background-color: #F3F3F3;
    }
</style>
