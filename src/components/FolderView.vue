<template>
  <div class="wrap">
    <div class="folder" :class="{'open':isOpen===true}"  v-on:click="toggle">
      <p class="folder-name">{{name}}</p>
    </div>
    <div class="folder-list" v-show="isOpen">
      <template v-for="folder in folders">
        <FolderView :name="folder.name" :folders="folder.folders" :files="folder.files"/>
      </template>
      <template v-for="file in files">
        <FileView :name="file.name" :type="file.type" :length="file.length"/>
      </template>
    </div>
  </div>
</template>

<script>
import FileView from "./FileView";
export default {
  name: 'FolderView',
  components: {FileView},
  props: {
    name: String,
    folders:Array,
    files:Array,
    type: String,
  },
  data: function() {
    return {
      isOpen: true,
    }
  },
  methods: {
    toggle: function() {
      this.isOpen = !this.isOpen;
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.wrap {
  position: relative;

  &::before {
    content: "";
    position: absolute;
    width: 1px;
    height: calc(100% - 47px);
    background-color: rgba(white, 0.1);
    left: 13px;
    top: 34px;
  }
}

.folder {
  position: relative;
  font-size: 18px;
  color: white;
  text-decoration: none;
  height: 40px;
  max-width: 180px;
  padding-left: 49px;
  margin-top: 0;
  margin-left: 10px;

  display: flex;
  align-items: center;
  justify-content: start;
  
  background-image: url("../img/folder.svg");
  background-repeat: no-repeat;
  background-position: 7%;
  background-size: 27px 27px;
  
  cursor: pointer;
  transition: all .1s ease-out;
  user-select: none;

  &::before {
    content: "";
    position: absolute;
    background-image: url("../img/arrow.svg");
    background-size: contain;
    background-repeat: no-repeat;
    width: 8px;
    height: 10px;
    left: 0;
    top: 18px;
    transition: transform .2s ease-out;
  }

  &:hover {
    color: rgba(white, 0.6);
  }

  &:active {
    color: rgba(white, 0.3);
  }
}

.folder.open {
  background-image: url("../img/folder-open.svg");

  &::before {
    transform: rotate(90deg);
  }
}

.folder-name {
  margin: 0;
  line-height: 20px;
}

.folder-list {
  padding-left: 38px;
}

</style>
