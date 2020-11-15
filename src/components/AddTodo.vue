<template>
    <div>
        <form @submit="addTodo">
            <input type="text" name="title" v-model="title" placeholder="Add Todo..." >
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>


<script>
// import uuid from 'uuid';

export default {
    name: "AddTodo",
    // props: ["todos"],
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();

            
            // Create new todo
            const newTodo = {
                // id: uuid.v4(),       No longer needed when using axios (automatically adds id)
                title: this.title,
                completed: false
            }

            console.log(newTodo);
            // Send to parent
            this.$emit('add-todo', newTodo);

            this.title = '';
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 2;
    }
</style>