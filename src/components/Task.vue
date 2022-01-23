<template>
  <div :class="[task.reminder ? 'reminder' : '', 'task']" @click="$emit('toggleReminder', task.id)">
    <h3>{{task.text}}
       <svg @click="onDelete(task.id)" aria-hidden="true" focusable="false" data-prefix="fas" data-icon="times" class="svg-inline--fa fa-times fa-w-11" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 352 512"><path fill="currentColor" d="M242.72 256l100.07-100.07c12.28-12.28 12.28-32.19 0-44.48l-22.24-22.24c-12.28-12.28-32.19-12.28-44.48 0L176 189.28 75.93 89.21c-12.28-12.28-32.19-12.28-44.48 0L9.21 111.45c-12.28 12.28-12.28 32.19 0 44.48L109.28 256 9.21 356.07c-12.28 12.28-12.28 32.19 0 44.48l22.24 22.24c12.28 12.28 32.2 12.28 44.48 0L176 322.72l100.07 100.07c12.28 12.28 32.2 12.28 44.48 0l22.24-22.24c12.28-12.28 12.28-32.19 0-44.48L242.72 256z"></path></svg>
    </h3>
    <p>{{task.day}}</p>
  </div>
</template>
<script>
import { library } from '@fortawesome/fontawesome-svg-core'
import { faUserSecret } from '@fortawesome/free-solid-svg-icons'

library.add(faUserSecret)
export default {
  name: 'Task',
  props: {
    task: Object
  },
  methods: {
    onDelete (id) {
      this.$emit('delete-task', id)
    }
  },
  emits: ['toggleReminder']
}
</script>
<style language='sass' scope>
.task {
  background-color: #f4f4f4;
  margin: 10px;
  padding: 10px 20px;
  cursor: pointer;
}
.task h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.task.reminder {
  border-left: 0.4vw solid green;
}
svg{
  width: 1.5em;
  height: 1.5em;
  color: red;
}
</style>
