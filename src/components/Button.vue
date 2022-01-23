<template>
    <button class="btn" @click="onClick()" :style="{ background: color}">{{text}}</button>
</template>
<script>
export default {
  name: 'Button',
  props: {
    text: String,
    color: String
  },
  methods: {
    onClick () {
      this.$emit('btn-click')
    }
  }
}
</script>
<style scoped>
.btn {
    background-color: seagreen;
    border: none;
    border-radius: 5px;
    width: 8em;
    color: seashell;
    font-size: 150%;
    float: right;
    cursor: pointer;
    position: absolute;
    right: 0;
    height: 3em;
    top: 1%;

    margin: 0;
    position: absolute;
    top: 50%;
    -ms-transform: translateY(-50%);
    transform: translateY(-50%);
}
</style>
