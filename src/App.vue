<template>
  <FolderView name="$" :folders="folders" :files="files" />
</template>

<script>
import FolderView from './components/FolderView.vue'
import data from './data/list';

export default {
  name: 'App',
  components: {
    FolderView
  },
  data: () => data
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  margin-top: 30px;
  margin-left: 30px;
  max-width: 380px;
}

body {
  background-color: #17141D;
}

</style>
