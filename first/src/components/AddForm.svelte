<script>
    import {createEventDispatcher} from "svelte";

    let value = '';

    const dispatch = createEventDispatcher();

    const handleSubmit = () => {
        dispatch('push-todo', value)
        value = ''
    }

    const keyUp = (event) => {
        if (event.key === 'Enter') {
            handleSubmit()
        }
    }
</script>

<div class="container">
    <input type="text" class="input" bind:value on:keyup={keyUp}>
    <button on:click={handleSubmit}>Create</button>
</div>

<style>

</style>