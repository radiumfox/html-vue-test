<template>
  <div class="file">
    <img class="file-icon" :src="showIcon(type)" width="25" height="25"/>
    <p class="file-name">{{ name }}</p>
    <p class="file-size">{{ convertBytes(length) }}</p>
  </div>
</template>

<script>
export default {
  name: 'FileView',
  props: {
    name: String,
    type: String,
    length: String,
  },
  methods: {
    showIcon(ext) {
      const ICONS = {
        "text/plain": require("../img/file-types/git.svg"),
        "image/svg": require("../img/file-types/picture.svg"),
        "image/jpeg": require("../img/file-types/picture.svg"),
        "application/json": require("../img/file-types/json.svg"),
        "image/png": require("../img/file-types/picture.svg"),
        "application/javascript": require("../img/file-types/js.svg"),
      };
      return ICONS[ext]
        ? ICONS[ext]
        : require("../img/file-types/file.svg");
    },

    convertBytes(bytes) {
      const sizes = ["B", "KB", "MB", "GB", "TB"];
      if (bytes == 0) return "0 B";
      const i = parseInt(Math.floor(Math.log(bytes) / Math.log(1024)));
      return Math.round(bytes / Math.pow(1024, i), 2) + " " + sizes[i];
    }
  }
}
</script>

<style scoped lang="scss">

.file {
  font-size: 18px;
  color: white;
  background-repeat: no-repeat;
  height: 39.85px;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: start;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  cursor: pointer;
  transition: color .1s ease-out;
  user-select: none;
  position: relative;
  margin-left: 10px;
  overflow-x: visible;
  
  &:hover {
    color: rgba(white, 0.6);
  }
}

.file {
  position: relative;
  overflow-x: hidden;
}

.file-name {
  margin: 0;
}

.file-icon {
  margin-right: 10px;
}

.file-size {
  visibility: hidden;
  transition: visibility .1s ease-out;
  font-size: 10px;
  color: rgba(white, 0.3);
  margin: 0 0 0 auto;
  padding: 0 15px;
}

.file:hover .file-size {
  visibility: visible;
}

</style>