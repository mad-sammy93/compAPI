<template>
  <div class="section">
    <h2>{{ userName }}</h2>
    <h3>{{ age }}</h3>
  </div>
</template>

<script>
import {
  computed,
  inject,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
} from 'vue';

export default {
  props: ['firstName', 'lastName', 'age'],
  // computed:{ ///Options API
  //     userName() {
  //         return this.firstName+ '  ' + this.lastName;
  //     }
  // },
  setup(props, context) {
    const uName = computed(function () {
      return props.firstName + ' ' + props.lastName;
    });

    function logging(mssg){
        console.log(mssg);
    }

    onBeforeMount(logging('onBeforeMount'));
    onMounted(logging('onMounted'));
    onBeforeUpdate(logging('onBeforeUpdate'));
    onUpdated(logging('onUpdated'));
    onBeforeUnmount(logging('onBeforeUnmount'));
    onUnmounted(logging('onUnmounted'));

    const age = inject('userAge');
    console.log(context, age);

    // context.emit('save-data',1); //works same as this.$emit('save-data',1);

    return { userName: uName };
  },
};
</script>
