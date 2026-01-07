<script>
    let { todos, remove } = $props();
</script>

<ul>
    {#each todos as todo}
        <li>
            <label>
                <input type="checkbox" bind:checked={todo.done} />
                <span>{todo.description}</span>
                <button
                    class="remove-button"
                    onclick={() => remove(todo)}
                    aria-label="Remove"><p>✖</p></button
                >
            </label>
        </li>
    {/each}
</ul>

<style>
    .remove-button {
        background-color: darkred;
    }
</style>
