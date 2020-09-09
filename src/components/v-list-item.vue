<template>

        <div :class="{'todo__list-item--completed': task.checked}" class="todo__list-item">
	    	<v-popup 
			v-if="isPopupVisible"
			:popupQuestion="'Вы уверены, что хотите удалить задачу'"
			:taskTitle="task.title"
			:rightBtnTitle="'Ok'"
			@deleteTask="deleteTask"
			@closePopup="isPopupVisible = !isPopupVisible"
			/>
          <div 
          	class="todo__list-item-check"
          	@click="checkTask"
          	>
            <i class="material-icons">check_circle</i>
            
          </div>
          <p>{{task.title}}</p>
          <div 
          	class="todo__list-item-remove"
          	@click="showPopup"
          >
            <i class="material-icons">delete_outline
			</i>
          </div>
        </div>
	
</template>
<script>
import vPopup from './v-popup'	
export default {
  name: 'v-list-item',
  props: {
  	task: {
  		type: Object,
  		default(){
  			return {}
  		}
  	}
  },
  data () {
    return {
    	isPopupVisible: false
    }
  },
  methods: {
  	checkTask(){
  		this.$emit('checkTask')
  	},
  	showPopup(){
  		this.isPopupVisible = true
  	},
  	deleteTask(){
  		this.$emit('deleteTask')

  	}
  },
  components: {
  	vPopup
  }
}
</script>
<style lang="scss">
</style>