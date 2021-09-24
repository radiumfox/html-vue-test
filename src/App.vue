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
  margin: 30px auto 0;
  max-width: 380px;
  border: 1px solid rgba(white, 0.1);
  background-image: url('./img/line.svg');
}

body {
  background-color: #17141D;
}

</style>
