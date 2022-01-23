<template>
    <header>
        <h1>{{title}}</h1>
        <Button @btn-click="$emit('toggle-add-task')" :color="showAddTask ? 'red' : 'seagreen'"
        :text="showAddTask ? 'Close' : 'Add Task'" />
    </header>
</template>
<script>
import Button from './Button.vue'
export default {
  name: 'Header',
  props: {
    title: String,
    showAddTask: Boolean
  },
  components: {
    Button
  },
  emits: ['toggle-add-task']
}
</script>
<style  scoped>
 header{
     display: flex;
     width: 100%;
     position: relative;
     margin-bottom: 1%;
 }
</style>
