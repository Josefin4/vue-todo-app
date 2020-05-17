<template>
  <div class="ListItem">
    <div class="ListItem-Text"><p>{{item.text}}</p></div>
    <button class="ListItem-Delete" @click="deleteItem(item.id)">x</button>
  </div>
</template>

<script>
export default {
  name: "ListItem",
  props: ["item"],
  methods: {
    deleteItem(id) {
      this.$emit("delete", id);
    }
  }
};
</script>

<style>
.ListItem {
  display: flex;
  align-items: center;
}
.ListItem-Text {
     color: black;
    width: 300px;
    background-color: white;
    height: 50px;
    margin: 10px auto;
    border-radius: 5px;
    font-family: Arial, Helvetica, sans-serif;
    border-style: solid;
    border-width: 1.5px;
    border-color: #dcdcdc;
   
}
.ListItem-Text p{
    left: 10px;
    bottom: 8px;
    position: relative;
    font-size: 19px;
    font-family: Arial, Helvetica, sans-serif;
}
.ListItem-Delete {
      width: 30px;
     height: 30px;
     background: red;
     border-radius: 5px;
     color: white;
     font-size: 15px;
      right: 490px;
     position: absolute;
     border: 0;
     font-weight: bolder;
}



</style>