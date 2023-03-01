<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
    <button @click="setAge">ChangeAge</button>
    <div>
      <input type="text" placeholder="First Name" @input="setFirstName" />
      <input type="text" placeholder="Last Name" @input="setLastName" />
    </div>
  </section>
</template>

<script>
import { ref, computed } from 'vue'; //isReactive , isRef

export default {
  setup() {
    const uAge = ref(31);
    const firstName = ref('asdsad');
    const lastName = ref('sadds');
    // const user = reactive({
    //   //reactive only works with objects
    //   name: 'Sambert',
    //   age: 99,
    // });


    const uName = computed(function(){
      return firstName.value + ' ' + lastName.value;
    })

    // function setNewAge() {
    //   user.age = 55;
    // }
    function setFirstName(event) {
      firstName.value = event.target.value;
    }
    function setLastName(event) {
      lastName.value = event.target.value;
    }

    // console.log(isReactive(user));
    // console.log(isReactive(uAge.value));
    console.log(uAge);

    // setTimeout(function () {
    //   // uName.value = 'Sam',
    //   // uAge.value = 33

    //   // ** with refs
    //   // user.value.name = "Sam";
    //   // user.value.age = 31;

    //   //**with reactive
    //   user.name = 'Sam';
    //   user.age = 31;
    // }, 2000);

    // const userRefs = toRefs(user);

    return {
      // user: user,
      userName: uName, //computed
      age: uAge, //change toRef
      // setAge: setNewAge, //button
      setFirstName,
      setLastName,
    };
  },
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
