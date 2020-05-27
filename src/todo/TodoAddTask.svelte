<script>
    import { tasks } from './store.js';

    let title;
    let storeTasks;

    tasks.subscribe(value => {
		storeTasks = value;
    });
    
    const addTaskHandler = e => {

        // Validation
        if (title == undefined || title.trim().length < 1) {
            const titleInput = e.target[0];
            titleInput.style.outlineColor = "red";
            titleInput.focus();
            return;
        }

        const task = {
            id: storeTasks.length++,
            title: title
        }

        tasks.update(value => {
            value = value.filter(n => n !== null);
            value.unshift(task);
            return value;
        });

        e.target[0].value = null;
    }
</script>

<form on:submit|preventDefault={addTaskHandler}>
    <div class="group">
        <input type="text" bind:value={title} class="input" placeholder="What do you need to do?" />
    </div>
    <div class="group">
        <input type="submit" class="input btn" value="Add Task" />
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
</style>