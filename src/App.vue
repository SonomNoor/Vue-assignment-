<template>
  <div
  >
<Not/>
<Card/>
<employee/>
<second/>

</div>


</template>


<script>
import Not from './components/Not.vue'
import HelloWorld from './components/HelloWorld'
import Card from './components/Card.vue'

import Vue from 'vue';
import employee from'./components/employee.vue'
import second from './components/second.vue'





export default {
  name: 'App',
  components: {
    HelloWorld,
    Not, Card,employee,second,
  }
}
</script>

<style>

</style>
