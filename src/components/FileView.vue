<template>
  <div class="file">
    <p >{{name}}</p>
  </div>
</template>

<script>
export default {
  name: 'FileView',
  props: {
    name: String
  }
}
</script>

<style scoped lang="scss">
.file {
  color: #333333;
  background-image: url("../img/file.svg");
  background-size: contain;
  background-repeat: no-repeat;
  background-position: 7%;
  width: 120px;
  height: 35px;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: start;
  margin-bottom: 15px;
  padding-left: 45px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  cursor: pointer;

  &:hover {
    color: rgba(#333333, 0.6);
  }
}

</style>