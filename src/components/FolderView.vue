<template>
<div class = "folder" :style="indent" @click="toggleChildren">
  <section v-if="isFolder">
    <icon-base 
    class="icon" 
    v-if="isOpen" 
    icon-name="openFolder" 
    iconColor = "#FFE500" 
    viewBox="0 0 512 512">
      <OpenFolderIcon />
    </icon-base>
   </section>

    <section v-if="isFolder">
     <icon-base 
     class="icon" 
     v-if="!isOpen"  
     icon-name="ClosedFolderIcon" 
     iconColor = "#FFE500" 
     viewBox="0 0 512 512">
       <ClosedFolderIcon />
      </icon-base>
   </section>

  <p>{{name}}</p>
  </div>

  <template v-for="folder in folders" v-if="showChildren">
    <FolderView :name="folder.name" :folders="folder.folders" :files="folder.files"  :depth="depth + 1" />
  </template>

  <template v-for="file in files" v-if="showChildren">
    <FileView :name="file.name" :depth="depth + 1"/>
  </template>

</template>

<script>
import FileView from "./FileView";
import IconBase from './IconBase.vue'
import OpenFolderIcon from './icons/OpenFolderIcon'
import ClosedFolderIcon from "./icons/ClosedFolderIcon.vue"
export default {
  name: 'FolderView',
  components: {
    FileView,
    IconBase,
    OpenFolderIcon,
    ClosedFolderIcon
  },
  props: {
    name: String,
    folders:Array,
    files:Array,
    depth: Number
  },
  data() {
      return { showChildren: false,
               isOpen: false }
    },
  computed: {
      indent() {
      return {transform: `translate(${this.depth * 50}px)`}
    },
  isFolder: function() {
    return this.folders 
    }
  },
  methods: {
    toggleChildren() {
      this.showChildren = !this.showChildren;
      this.isOpen = !this.isOpen;
      }

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

 @import url('https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,300;1,300&family=PT+Sans&display=swap');


.folder {
  height: 30px;
  display: flex;
  align-items: center;
  border: 1px double rgba(29, 115, 115, 0);
  border-radius: 5px;
  background-color:rgba(92, 204, 204, 0);
  transition: background-color 0.2s ease;
  border-width: 0 0 1px 1px;
  margin: 0 0 0 1.2em;
}
.folder:hover{
  color: orangered;
  border: 1px double rgba(29, 115, 115, 0.3);
  border-radius: 5px;
  background-color:rgba(92, 204, 204, 0.3);
  cursor: pointer;
  border-width: 0 0 1px 1px;
  margin: 0 0 0 1.2em;
}
.folder_checkbox {
  padding-right: 10px;
}
.icon {
  padding-right: 15px;
}

</style>
