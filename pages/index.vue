<script setup>
    import { ref } from 'vue'

    // give each todo a unique id
    let id = 0

    const newTodo = ref('')
    const todos = ref([
    { id: id++, text: 'Learn HTML' },
    { id: id++, text: 'Learn JavaScript' },
    { id: id++, text: 'Learn Vue' }
    ])

    function addTodo() {
        // push to list
        // to access whatever is inside a ref initialized element, it is 'value'
        // ref({ name: 'Batman' }) creates a ref that stores an object. You can access the object from the ref using hero.value.
        // https://dmitripavlutin.com/ref-in-vue/
        todos.value.push({id: id++, text: newTodo.value});

        //resets variable to empty string
        newTodo.value = ''
    }

    function removeTodo(todo) {
        // remove from list. 1 because limited to 1 removal from id point 
        todos.value.splice(todo.id, 1);
    }
</script>

<template>
    <!-- submit.prevent to avoid reloading the page on form submit -->
    <form @submit.prevent="addTodo">
        <!-- This v-model attribute binds to value in JS -->
        <input v-model="newTodo" required placeholder="new todo">
        <button>Add Todo</button>
    </form>
    <ul>
        <li v-for="todo in todos" :key="todo.id">
            {{ todo.text }}
            <button @click="removeTodo(todo)">X</button>
        </li>
    </ul>
</template>