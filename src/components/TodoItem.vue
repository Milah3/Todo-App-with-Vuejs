<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p> 
            <input type="checkbox" v-on:change="$emit('mark-complete', todo)" /> 
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" class="del">x</button>
        </p>

    </div>    
</template>

<script>
export default {
    name: 'TodoItem',
    props: ['todo'], 
    methods: {
        // markComplete() {
        //     this.todo.completed = !this.todo.completed;
        //     // let localTodo = this.todo;
        //     // console.log("marked Complete");
        //     // localTodo.completed = !localTodo.completed;
        //     // this.$emit("is-complete", this.todo);
        // }

        // ^ The above didn't work. Moved it down thru props to parent Home.vue and it worked
    }
}
</script>

<style scoped>
    .todo-item {
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }
    .is-complete {
        text-decoration: line-through;
    }
    .del {
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }

</style>