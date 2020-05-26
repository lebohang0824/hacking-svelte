<script>

</script>

<form on:submit|preventDefault>
    <div class="group">
        <input type="text" class="input" placeholder="What do you need to do?" />
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