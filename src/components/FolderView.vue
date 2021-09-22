<template>
 <div class="wrap">
    <div class="folder" :class="{'open':isOpen===true}"  v-on:click="toggle">
      <p>{{name}}</p>
    </div>
    <div class="folder-list" v-show="isOpen">
      <template v-for="folder in folders">
        <FolderView :name="folder.name" :folders="folder.folders" :files="folder.files"/>
      </template>
      <div class="file-wrap">
        <template v-for="file in files">
          <FileView :name="file.name"/>
        </template>
      </div>
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
    files:Array
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

    fade: function() {
      const lists = document.querySelectorAll(".folder-list");
      lists.forEach(item, () => {
       item.style.transition = "all 2s"; 
      });
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.folder {
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: start;
  color: white;
  width: 120px;
  height: 30px;
  padding-left: 60px;
  background-image: url("../img/folder.svg");
  background-repeat: no-repeat;
  background-position: 10%;
  background-size: contain;
  text-decoration: none;
  margin-top: 0;
  margin-bottom: 15px;
  position: relative;
  cursor: pointer;

  // background-color: #21212A;
  
  &::before {
    content: "";
    position: absolute;
    background-image: url("../img/arrow.svg");
    background-size: contain;
    background-repeat: no-repeat;
    width: 6px;
    height: 10px;
    left: 0;
    transition: transform .2s ease-out;
  }

  &:hover {
    color: rgba(white, 0.6);
  }
}

.folder.open {
  &::before {
    transform: rotate(90deg);
  }
}


.folder-list {
  padding-left: 40px;
  
}


</style>
