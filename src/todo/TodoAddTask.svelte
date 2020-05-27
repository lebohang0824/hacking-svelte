<script>
    import { tasks } from './store.js';

    let title;
    let count = 1;
    let storeTasks;

    tasks.subscribe(value => {
		storeTasks = value;
    });
    
    const addTaskHandler = e => {
        if (title == null || title.trim().length < 1) {
            e.target[0].focus();
            return;
        }

        const task = {
            id: count++,
            title: title,
            finished: false
        }

        tasks.update(value => {
            value = value.filter(n => n !== null);
            value.unshift(task);
            return value;
        });

        e.target[0].value = null;
        title = null;
    }
</script>

<form on:submit|preventDefault={addTaskHandler}>
    <div class="group">
        <input type="text" bind:value={title} class="input " class:empty="{!title|| title.trim().length < 1}" placeholder="What do you need to do?" />
    </div>
    <div class="group">
        <input type="submit" disabled={!title|| title.trim().length < 1} class="input btn" value="Add Task" />
    </div>
</form>

<style>
    form {
        display: grid;
        grid-template-columns: 70% 30%;
    }
    .group {
        padding: 10px;
        background-color: #F9F8F9;
    }
    .input {
        margin: 0;
        width: 100%;
        padding: 10px 15px;
        box-sizing: border-box;
    }
    .btn {
        cursor: pointer;
    }
    .empty {
        outline-color: red;
    }
</style>