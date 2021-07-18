<template>
    <form @submit="addItem">
        <input 
            type="text" 
            placeholder="New to do...." 
            v-model="title" 
            @input="check"
        >
        <input type="submit" value="Add" class="add-btn">
    </form> 
</template>

<script>
//import
import {ref} from 'vue'
// import {v4 as uuidv4} from 'uuid'

export default {
    name: 'AddTodo',
    setup(props,context){
        const title = ref('')
        
        const addItem = event => {
            event.preventDefault()

            const newItem = {
                title: title.value,
                completed: false,
            }
            context.emit('add-todo',newItem)

            //reset input nhap vao thanh rong
            title.value = ''
        }
        return {
            title,
            addItem,
        }
    } 
}
</script>

<style>
form {
    display: flex;
}

input[type='text'] {
    flex: 10;
    padding: 5px;
}

input[type='submit'] {
    flex: 2;
     
}
</style>