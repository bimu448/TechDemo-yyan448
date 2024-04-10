<template>
  <div class="app">
    <h1>the first vue app</h1>
    <Advice />
  </div>
</template>
<script>
//import Person from "./components/Person.vue";
import Advice from "./components/Advice.vue";
export default {
  name: "App",
  components: {
    Advice,
  },
};
</script>
