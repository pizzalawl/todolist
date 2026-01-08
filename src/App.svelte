<script>
    import List from "./lib/List.svelte";
    let todos = $state([
        { done: false, description: "write some docs" },
        { done: false, description: "start writing blog post" },
        { done: false, description: "buy some milk" },
        { done: false, description: "mow the lawn" },
        { done: false, description: "feed the turtle" },
        { done: false, description: "fix some bugs" },
    ]);

    const remove = (todo) => {
        todos.splice(todos.indexOf(todo), 1);
    };
</script>

<main>
    <div class="centerbox">
        <h1 style="text-align: center;">To-Do List</h1>
        <div id="lists">
            <List todos={todos.filter((t) => !t.done)} {remove} />
            <List todos={todos.filter((t) => t.done)} {remove} />
        </div>
        <input
            type="text"
            placeholder="yo, watchu need to do"
            onkeydown={(e) => {
                if (e.key !== "Enter") return;

                todos.push({
                    done: false,
                    description: e.currentTarget.value,
                });

                e.currentTarget.value = "";
            }}
            id="input"
        />
    </div>
</main>

<style>
    #lists {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
    }
    #input {
        margin: 5%;
        margin-right: 7%;
    }
    .centerbox {
        display: flex;
        flex-direction: column;
        flex-grow: 3;
        font-family: Arial, Helvetica, sans-serif;
        width: 40rem;
        margin: 0 auto;
        margin-top: 3rem;
        padding-left: 2rem;
        padding-top: 1rem;
        background-color: #272652;
        border-radius: 5%;
    }
</style>
