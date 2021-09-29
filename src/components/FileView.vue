<template>
<div class="file" :style="indent">
  <section>
    <icon-base
      class="icon" 
      :icon-name="getIconName"
      :viewBox="viewBox">
        <component :is="getIconName" @getVieBox="getViewBox($event)"> </component>
    </icon-base >
  </section>
  <p>{{name}}</p>
  <!-- <p>{{size}} kb</p> -->
</div>
</template>

<script>
import IconBase from './IconBase.vue'
import JpegIcon from './icons/JpegIcon.vue'
import JpgIcon from './icons/JpgIcon.vue'
import PngIcon from './icons/PngIcon.vue'
import SvgIcon from './icons/SvgIcon.vue'
import BrowserslistrcIcon from './icons/BrowserslistrcIcon.vue'
import GitignoreIcon from './icons/GitignoreIcon.vue'
import JsIcon from './icons/JsIcon.vue'
import JsonIcon from './icons/JsonIcon.vue'

export default {
  name: 'FileView',
    components: {
    IconBase,
    JpegIcon,
    JpgIcon,
    PngIcon,
    SvgIcon,
    BrowserslistrcIcon,
    GitignoreIcon,
    JsIcon,
    JsonIcon
  },
  props: {
    name: String,
    depth: Number,
    iconName: String,
    size: String
  },
  data() {
    return {
      viewBox: "0 0 300 300"
    }
  },
    computed: {
      indent() {
      return `margin-left:${this.depth * 50}px`
    },
    getIconName() {
      return this.iconName + "Icon"
    }

  },
  methods: {
    getViewBox(event) {
      this.viewBox = event
    }
  }
}
</script>

<style scoped lang="scss">
.file{
  height: 30px;
  display: flex;
  align-items: center;
  border: 1px double rgba(34, 133, 133, 0);
  border-radius: 5px;
  background-color:rgba(92, 204, 204, 0);
  transition: background-color 0.2s ease;
  font-size: 11pt;
}
.file:hover{
  color: orangered;
  border: 1px double rgba(28, 133, 133, 0.3);
  border-radius: 5px;
  background-color:rgba(92, 204, 204, 0.3);
  cursor: pointer;
}
.icon {
  padding-right: 10px;
  padding-left: 10px;
}
</style>
