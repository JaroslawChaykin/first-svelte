<script>
    import {createEventDispatcher} from "svelte";
    import {flip} from "svelte/animate";

    export let todo;

    const {id, value, checked} = todo;

    const dispatch = createEventDispatcher();
    const setChecked = (target) => {
        dispatch('set-checked', target)
    }

    const deleteTodo = (target) => {
        dispatch('delete-todo', target)
    }

</script>


<td>
    <input type="checkbox" on:change={() => setChecked(id)} {checked}>
</td>

<td>
    <h1>{value}</h1>
</td>

<td>
    <button on:click={() => deleteTodo(id)}>Delete</button>
</td>

<style>

</style>
