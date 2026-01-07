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
        <h1>To-Do List</h1>
        <List todos={todos.filter((t) => !t.done)} {remove} />
        <List todos={todos.filter((t) => t.done)} {remove} />
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
        />
    </div>
</main>

<style>
    .centerbox {
        font-family: Arial, Helvetica, sans-serif;
        height: 40rem;
        width: 80rem;
        margin: 0 auto;
        margin-top: 3rem;
        padding-left: 2rem;
        padding-top: 1rem;
        background-color: #b87af0;
        border-color: #a047ed;
        border-radius: 5%;
        border-width: 8px;
    }
</style>
