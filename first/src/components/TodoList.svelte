<script>
    import TodoItem from "./TodoItem.svelte";
    import {flip} from "svelte/animate";

    export let list;
</script>

<!--{#each list as todo (todo.id)}-->
<!--    <div animate:flip={{duration: 150}}>-->
<!--        <TodoItem {todo} on:set-checked on:delete-todo />-->
<!--    </div>-->
<!--{:else }-->
<!--    <p>No one element</p>-->
<!--{/each}-->

<table>
    <thead>
        <tr>
            <td colspan="1">Checked</td>
            <td colspan="1">Title</td>
            <td class="td-btn" colspan="1">Actions</td>
        </tr>
    </thead>
    <tbody>
    {#each list as todo (todo.id)}
        <tr animate:flip={{duration: 150}} aria-colcount="5">
            <TodoItem {todo} on:set-checked on:delete-todo  />
        </tr>
    {:else }
        <p>No one element</p>
    {/each}
    </tbody>
</table>

<style>
    table {
        width: 100%;
    }

    .td-btn {
        width: 10%;
    }
</style>
