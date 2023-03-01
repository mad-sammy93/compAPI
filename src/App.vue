<template>
  <section class="container">
    <h2>{{ user.name }}</h2>
    <h3>{{ user.age }}</h3>
  </section>
</template>

<script>
import { reactive } from 'vue';

export default {

  setup() {
    const user = reactive({ //reactive only works with objects
      name:'Sambert',
      age: 99
    })

    console.log(user);
    setTimeout(function(){
      // uName.value = 'Sam',
      // uAge.value = 33

      // ** with refs
      // user.value.name = "Sam";
      // user.value.age = 31;

      //**with reactive
      user.name = "Sam";
      user.age = 31;
    }, 2000);

    return { user:user}
  }
  // data() {
  //   return {
  //     userName: 'Maximilian',
  //   };
  // },
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>