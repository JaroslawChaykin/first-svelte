<script>
    import AddForm from "./components/AddForm.svelte";
    import {onMount} from "svelte";
    import TodoList from "./components/TodoList.svelte";

    let items = [];

    const pushTodo = ({detail}) => {
        items.push({
            id: new Date(),
            value: detail,
            checked: false,
        })
        items = items
    }

    const deleteTodo = ({detail}) => {
        items = items.filter((item) => {
            if (detail !== item.id) {
                return item
            }
        })
    }

    const setCheckedTodo = ({detail}) => {
        items = items.filter((item) => {
            if (detail === item.id) {
                item.checked = !item.checked
            }

            return item
        })
    }

    $: items.length > 0 && localStorage.setItem('items', JSON.stringify(items));

    $: allTodo = () => {
        return items.filter(item => !item.checked)
    }

    $: checkedTodo = () => {
        return items.filter(item => item.checked)
    }

    onMount(() => {
        items = JSON.parse(localStorage.getItem('items')) || [];
    })

</script>

<main>
    <AddForm on:push-todo={pushTodo}/>
    <h1>All Todo</h1>
    <TodoList list={allTodo()} on:set-checked={setCheckedTodo} on:delete-todo={deleteTodo}/>

    <h1>Checked Todo</h1>
    <TodoList list={checkedTodo()} on:set-checked={setCheckedTodo} on:delete-todo={deleteTodo}/>

</main>

<style>

</style>