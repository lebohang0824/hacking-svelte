<script>
    import { tasks } from './store.js';
    export let task;

    let storeTasks;
    tasks.subscribe(value => {
		storeTasks = value;
    });
    
    const deleteTaskHandler = () => {
        tasks.update(value => {
            console.log(task.id);
            return value.filter(selected => selected.id !== task.id);
        });
    }

</script>

<div class="task">
    <div class="done">
        <input class="checkbox" type="checkbox" />
    </div>
    <div class="title">{task.title}</div>
    <div class="delete" on:click={deleteTaskHandler}>x</div>
</div>

<style>
    .task {
        padding: 10px;
        display: grid;
        border-radius: 5px;
        margin-bottom: 5px;
        box-sizing: border-box;
        background-color: #D0D0D0;
        grid-template-columns: 20px auto 20px;
    }
    .done {
        padding: 1px;
        text-align: center;
    }
    .title {
        padding: 0 5px;
    }
    .delete {
        padding: 1px;
        color: red;
        opacity: 0.3;
        cursor: pointer;
        font-weight: bold;
        text-align: center;
    }
    .delete:hover {
        opacity: 1;        
    }
    .checkbox {
        cursor: pointer;
    }
</style>