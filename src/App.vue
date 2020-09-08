<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">

    <!-- Народ, тепер спробуємо зробити наш TodoList разом з Firebase (без чекбоксів); Нам потрібно використати 3 метода get, post, delete;
    При загрузці сторінки має показати наш тудуліст і відразу ж усі тудушки які в нас є (можемо викликати this.$http.get('') в хуці beforeMounted());
    При кліку на кнопку маємо добавляти нашу тудушку в базу (тобто на клік маємо викликати метод post);
    І відповідно при клікові delete маємо видалити нашу тудушку: Потрібно в v-for крутити наш масив і при клікові delete видаляти нашу тудушку this.$http('link/${item.id}') -->
    
    <h1>HomeWork - 3</h1>

    <input type="text" v-model="todo">
    <button @click="add" v-if="arrayToDo.length <10">Add</button>
  
    <ul>
      <li v-for="(todos, i) in arrayToDo" :key="i">
        {{todos.item}} 
         <button @click="remove(i)">Delete</button>
      </li>
    </ul>

  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      arrayToDo: [],
      todo: "",
    }
  },

  beforeMount () {
      this.$http.get('https://hw3-vue.firebaseio.com/.json')
      .then((res) => {
        return res.json();
      })
      .then((res) => {
        Object.values(res).forEach((el) => this.arrayToDo.push(el));
      })
  },

  methods: {
    
    add () {
      this.arrayToDo.push({item:this.todo});
      this.$http.post('https://hw3-vue.firebaseio.com/.json',{item:this.todo});
      this.todo = "";
    },

    remove (i) {
      this.arrayToDo.splice(i, 1);
      this.$http.get('https://hw3-vue.firebaseio.com/.json')
      .then((res) => {
        return res.json();
      })
      .then((res) => {
        this.$http.delete(`https://hw3-vue.firebaseio.com/${Object.keys(res)[i]}.json`)
      })
    }
  },

}

</script>



<style>

</style>

