<template>
    <form @submit="onSubmit" class="add-form">
        <div class="form-control">
            <label>Task</label>
            <input type="text" v-model="text" name="text" placeholder="Add Task" />
        </div>
        <div class="form-control">
            <label> Day & Time</label>
            <input type="text" name="day" v-model="day" placeholder="Add day and time" />
        </div>
        <div class="form-control form-control-check">
            <label>Set reminder</label>
            <input type="checkbox" name="reminder" v-model="reminder"/>
        </div>
        <input type="submit" value="Save task" class="btn btn-block" />
    </form>
</template>
<script>
export default {
  name: 'AddTask',
  data () {
    return {
      text: '',
      day: '',
      reminder: false
    }
  },
  methods: {
    onSubmit (e) {
      e.preventDefault()
      if (!this.text) {
        alert('Please add a task')
        return
      }
      const newTask = {
        id: Math.floor(Math.random() * 100000),
        text: this.text,
        day: this.day,
        reminder: this.reminder
      }
      this.$emit('add-task', newTask)
      this.text = ''
      this.day = ''
      this.reminder = false
    }
  }
}
</script>
<style scoped>
.add-form {
    margin-bottom: 40px;
}
.form-control {
    margin: 20px 1vw 20px 0;
}
.form-control label {
    display: block;
    font-size: 110%;
}
.form-control input{
    width: 100%;
    height: 40px;
    margin: 5px;
    padding: 3px 7px;
    font-size: 110%;
    margin-right: 0px;
}
.form-control-check {
    display: flex;
    justify-content: space-between;
}
.form-control-check label {
    flex: 1;
}
.form-control-check input {
    flex: 2;
    height: 40px;
    margin-left: -100%;
}

.btn{
    width: 90%;
    background-color: black;
    color: seashell;
    margin: 15px;
    font-size: 150%;
    cursor: pointer;
    height: 3em;
    margin-left: 5vw;
    border-radius: 5px;
}
</style>
