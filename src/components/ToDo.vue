

<template>
  <div id="app">
    <div class="ToDo">
      <div class="ToDo-Container">
        <div class="ToDo-Content">
          <ListItem v-for="item in list" :item="item" @delete="onDeleteItem" :key="item.id" />
        </div>
        <input type="text" v-model="todo" v-on:keyup.enter="createNewToDoItem" placeholder="Enter a task" />
        <button class="ToDo-Add" @click="createNewToDoItem">Add</button>
      </div>
    </div>
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";
export default {
  name: "ToDo",
  components: {
    ListItem
  },
  data() {
    return {
      list: [],
      todo: "",
    };
  },
  methods: {
    createNewToDoItem() {
      if (!this.todo) {
        return;
      }
      const newId = this.list.length
        ? Math.max.apply(null, this.list.map(t => t.id)) + 1
        : 1;
      this.list.push({ id: newId, text: this.todo });
      this.todo = "";
    },
    onDeleteItem(id) {
      this.list = this.list.filter(item => item.id !== id);
    }
    
  }
};
</script>

<style>
body {
  background-color:#dcdcdc;
}

.ToDo {
 background-color: white;
  min-height: 500px;
  width: 400px;
  margin: 40px auto;
  padding: 20px;
  font-family: Arial, Helvetica, sans-serif;
}

.ToDo-Add {
 height: 30px;
width: 60px;
border-radius: 5px;
border: 0;
background-color:#6495ed;
font-weight: bolder;
color: white;
margin-left: 40%;
margin-top: 5px;
}
.ToDo-Add:hover {
  box-shadow: none;
}
.ToDo-Container {
  width: 80%;
  margin: 0 auto;
}
input {
   background-color: #dcdcdc;
  border: 0;
  width: 200px;
  height: 50px;
  padding: 0 20px;
  margin: auto;
  margin-left: 40px;
  margin-top: 74px;
  font-size: 18px;
  border-radius: 10px;
  color: black;
  clear: both;
}

input::placeholder{
  color: darkgrey;
}
</style>