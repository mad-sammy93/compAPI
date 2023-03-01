<template>
    <div class="section">
        <h2>{{ userName }}</h2>
        <h3>{{ age }}</h3>
    </div>
</template>

<script>
import {computed} from 'vue';
export default{
    props: ['firstName', 'lastName', 'age'],
    // computed:{ ///Options API
    //     userName() {
    //         return this.firstName+ '  ' + this.lastName;
    //     }
    // },
    setup(props) {
        const uName = computed(function() {
            return props.firstName+ ' '+ props.lastName;
        });

        return {userName: uName}
    }
}
</script>