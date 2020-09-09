<template>
	<div class="todo__add-field">
        <input 
        	type="text" 
        	placeholder="Введите текст задачи..." 
        	maxlength="70"
        	v-model.trim="taskTitle"
        >
        <button class="todo__add-field-button"
        @click="addTask"
        >
          <i class="material-icons">add</i>
        </button>
      </div>
</template>
<script>
export default {
  name: 'v-task-field',
  data () {
    return {
    	taskTitle: ''
    }
  },
  methods: {
  	addTask(){
  		if (this.taskTitle === '') return 
  		this.$emit('addTask', this.taskTitle)
  		this.taskTitle = ''
  	}
  }
}
</script>
<style lang="scss">
</style>