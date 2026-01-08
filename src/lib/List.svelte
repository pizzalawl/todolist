<script>
    import removepic from "../assets/remove.svg";
    let { todos, remove } = $props();
</script>

<ul>
    {#each todos as todo}
        <li style="list-style-type: none; margin: 1rem;">
            <label>
                <input type="checkbox" bind:checked={todo.done} />
                <span>{todo.description}</span>
                <button class="remove-button" onclick={() => remove(todo)}
                    ><div>Delete</div></button
                >
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
    }
    button div {
        position: relative;
        bottom: 0.1rem;
        border-color: transparent;
        background-color: darkred;
        border-radius: 5px;
        width: 4rem;
        height: 1rem;
    }
    button div:hover {
        opacity: 0.8;
    }
</style>
