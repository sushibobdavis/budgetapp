<template>
  <div class="home">
    <CreateBudget msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import CreateBudget from '@/components/CreateBudget.vue';

export default {
  name: 'home',
  components: {
    CreateBudget,
  },
};
</script>
