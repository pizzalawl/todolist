<script>
    import removepic from "../assets/remove.svg";
    let { todos, remove } = $props();
</script>

<ul>
    {#each todos as todo}
        <li style="list-style-type: none;">
            <label>
                <input type="checkbox" bind:checked={todo.done} />
                <span>{todo.description}</span>
                <button class="remove-button" onclick={() => remove(todo)}>
                    <img src={removepic} alt="remove" />
                </button>
            </label>
        </li>
    {/each}
</ul>

<style>
    .remove-button {
        background-color: transparent;
    }
    input[type="checkbox"] {
        accent-color: green;
    }
    button {
        border-color: transparent;
        position: relative;
        right: 1%;
        top: 2%;
        width: 15%;
        height: 15%;
    }
    button img {
        width: 100%;
        height: 100%;
    }
    button img:hover {
        opacity: 0.8;
    }
</style>
