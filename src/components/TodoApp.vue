<template>
    <div>
  
      <div class="item">
        <p>Nowe todo: {{ newItem }}</p>
        <input type="text" placeholder="todo" v-model="newItem">
        <button @click="addItem">Dodaj</button>
      </div>
  
      <TodoItem  
        v-for="item in items" 
        :key="item.id"
        :item="item"
        @removeClicked="removeItem"
        />
  
    </div>
  </template>
  
  <script>
  import TodoItem from './TodoItem.vue'

  export default {
    components: {
        TodoItem: TodoItem 
    },
    data() {
      return {
        newItem: '',
        items: [
          { title: 'Zrobić zakupy', completed: false, id: 1},
          { title: 'Posprzątać', completed: true, id: 2}
        ]
      }
    },
    methods: {
      addItem() {
        this.items.push({ 
          title: this.newItem, 
          completed: false, 
          id: Math.random() 
        })
        this.newItem = ''
      },
      removeItem(id) {
        const index = this.items.findIndex(el => el.id === id)
        this.items[index].completed = true
      }
    }
  }
  
  </script>
  
  <style>
    .item {
      border: 1px solid #62028f;
      margin: 8px;
      padding: 10px;
    }
    .completed {
      opacity: 0.5;
    }
    .completed h2 {
      text-decoration: line-through;
    }
  </style>