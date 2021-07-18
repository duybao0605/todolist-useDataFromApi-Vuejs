<template>
    <p :class="['todo-item', todoProps.completed ? 'is-compeleted' : '']">
        <input
        type="checkbox"
        :checked="todoProps.completed"
        @change="markItemCompleted"
        />
        {{ todoProps.title }}
        <button class="del-btn" @click="deleteItem">Delete</button>
    </p>
    
</template>

<script>
// import {ref} from 'vue'

export default {
  name: 'TodoItem',
  props: ['todoProps'],
  setup(props, context) {
    const markItemCompleted = () => {
      context.emit('item-completed', props.todoProps.id)
    }
    const deleteItem = () => {
        context.emit('delelte-item',props.todoProps.id)
    }
    return {
      markItemCompleted,
      deleteItem,
    }
  }
}
</script>

<style>
.todo-item {
    background: #f4f4f4;
    padding: 10px;
    margin: 0;
    border-bottom: 1px #ccc dotted;
}

.is-compeleted{
    text-decoration: line-through;
}

.del-btn {
    background: red;
    color: aliceblue;
    padding: 8px;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    float: right;
}
</style>