<script setup>
  import {ref} from 'vue'
  const myArray = ref([])
  const name = ref('')
  const input_content = ref('')
  const input_category = ref(null)

  const addtodo = () =>{
    if(input_content.value.trim() === ''|| input_category.value == null){
      return
    }

    myArray.value.push({
      content: input_content.value,
      category: input_category.value,
    })

    input_content.value = ''
    input_category.value = null
  }


</script>

<template>
  
  <main class="app">

    <section class="greeting">
      <h2 class="title">
        Welcome back, <input type="text" placeholder="Enter Name" v-model="name">
      </h2>
      
    </section>


    <section class="create-todo">
      <h3>CREATE A TODO LIST</h3>
      <form @submit.prevent ="addtodo">
        <h4>Whats on your to do list?</h4>
        <input type="text" placeholder="e.g., Make a Video" v-model="input_content"/>


        <h4>Pick a category</h4>
        <div class="options">
          <label>
            <input type="radio" name="category" value="business" v-model="input_category">
            <span class="bubble business"></span>
            <div>Business</div>
          </label>
          <label>
            <input type="radio" name="category" value="personal" v-model="input_category">
            <span class="bubble personal"></span>
            <div>Personal</div>
          </label>
        </div>
        <input type="submit" value="Add To Do"/>
      </form>

    </section>

    <section class="todo-list">


    </section>

  </main>
</template>


