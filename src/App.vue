<template>
  <section class="container">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
    <button @click="setAge">ChangeAge</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName" />
      <input type="text" placeholder="Last Name"  ref="lastNameInput"/>
      <button @click="setLastName">Set Last Name</button>
    </div>
  </section>
</template>

<script>
import { ref, computed , watch } from 'vue'; //isReactive , isRef

export default {
  setup() {
    const uAge = ref(31);
    const firstName = ref('Sammy');
    const lastName = ref('Khadeira');
    const lastNameInput = ref(null);
    // const user = reactive({
    //   //reactive only works with objects
    //   name: 'Sambert',
    //   age: 99,
    // });


    const uName = computed(function(){
      return firstName.value + ' ' + lastName.value;
    })

    watch([uAge,uName], function(newValue,  oldValue) {
      console.log(oldValue[0]+ ' ' + newValue[0]);
      console.log(oldValue[1]+ ' ' + newValue[1]);
    });

    function setNewAge() {
      uAge.value = 55;
    }

    function setLastName() {
      lastName.value = lastNameInput.value.value;
    }
    // function setFirstName(event) {
    //   firstName.value = event.target.value;
    // }
    // function setLastName(event) {
    //   lastName.value = event.target.value;
    // }

    // console.log(isReactive(user));
    // console.log(isReactive(uAge.value));

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
      setAge: setNewAge, //button
      setLastName,
      // setFirstName,
      // setLastName,
      firstName,
      lastName,
      lastNameInput
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
