<script>
import Vue from 'vue';
import VueModal from '@/vueModal.vue';

export default Vue.extend({
  name: 'ServeDev',
  components: {
    VueModal
  }
});
</script>

<template>
  <div id="app">
    <vueModal />
  </div>
</template>
