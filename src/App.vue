<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">

    <!-- Народ, тепер спробуємо зробити наш TodoList разом з Firebase (без чекбоксів); Нам потрібно використати 3 метода get, post, delete;
    При загрузці сторінки має показати наш тудуліст і відразу ж усі тудушки які в нас є (можемо викликати this.$http.get('') в хуці beforeMounted());
    При кліку на кнопку маємо добавляти нашу тудушку в базу (тобто на клік маємо викликати метод post);
    І відповідно при клікові delete маємо видалити нашу тудушку: Потрібно в v-for крутити наш масив і при клікові delete видаляти нашу тудушку this.$http('link/${item.id}') -->
    
    <h1>HomeWork - 3</h1>
    <div>
      
    </div>


  </div>
</template>

<script>


export default {
  name: 'App',
  components: {
    
  }
}
</script>

<style>

</style>
