<template>
  <p class="file" :style="indent">{{name}}</p>
</template>

<script>
export default {
  name: 'FileView',
  props: {
    name: String,
    depth: Number
  },
    computed: {
      indent() {
      return {transform: `translate(${this.depth * 50}px)`}
    }
  }
}
</script>

<style scoped lang="scss">
.file{
  height: 30px;
  display: flex;
  align-items: center;
  border: 1px double rgba(29, 115, 115, 0);
  border-radius: 5px;
  background-color:rgba(92, 204, 204, 0);
  transition: background-color 0.2s ease;
}
.file:hover{
  color: orangered;
  border: 1px double rgba(29, 115, 115, 0.3);
  border-radius: 5px;
  background-color:rgba(92, 204, 204, 0.3);
  cursor: pointer;
}
</style>
