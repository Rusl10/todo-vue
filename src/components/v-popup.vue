<template>
	<div 
		class="popup-wrapper"
		ref="popup-wrapper"
	>
		<div class="v-popup">
			<div class="v-popup__header">
				<span>
					<i 
						class="material-icons close-icon"
						@click="closePopup"
						>close</i></span>
				</div>
			<div class="v-popup__content">

				{{ popupQuestion }} "{{ taskTitle }}" ?
				
			</div>
			<div class="v-popup__footer">
				<button 
					class="close-modal"
					@click="closePopup"
				>close</button>
				<button 
					class="submit-btn"
					@click="deleteTask"
				>{{rightBtnTitle}}</button>
			</div>
		</div>
	</div>
</template>
<script>
export default {
  name: 'v-popup',
  props: {
  	popupQuestion: {
  		type: String,
  		default: 'Удалить задачу?'
  	},
  	taskTitle: {
  		type: String,
  		default: ''
  	},
  	rightBtnTitle: {
  		type: String,
  		default: "Да"
  	}
  },
  data () {
    return {
    }
  },
  methods: {
  	deleteTask(){
  		this.$emit('deleteTask')
  		this.closePopup()
  	},
  	closePopup(){
  		this.$emit('closePopup')
  	}
  },
  mounted(){
  	document.addEventListener('click', (item) => {
  		if (item.target === this.$refs['popup-wrapper']) {
  			this.$emit('closePopup')
  		}
  	})
  },
  beforeDestroy(){
  	document.removeEventListener('click', (item) => {
  		if (item.target === this.$refs['popup-wrapper']) {
  			this.$emit('closePopup')
  		}	
  	})
  }
}
</script>
<style lang="scss">
.popup-wrapper{
	display: flex;
	position: fixed;
	justify-content: center;
	align-items: center;
	background: rgba(64,64,64, .4);
	top: 0;
	left: 0;
	right: 0;
	bottom: 0;
}
.v-popup {
	padding: 16px 40px;
	box-sizing: border-box;
	width: 400px;
	position: fixed;
	z-index: 100;
	background: #fff;
	top: 50%;
	transform: translate(-50%, -50%);
	left: 50%;
	box-shadow: 0 0 17px #e7e7e7;
	&__header, &__footer {
		display: flex;
		justify-content: space-between;
		align-items: center;
	}
	&__header{
		justify-content: flex-end;
	}
	&__content {
		display: flex;
		justify-content: center;
		align-items: center;
		margin-top: 20px;
		margin-bottom: 30px;
		text-align: center;
	}
	.submit-btn, .close-modal {
		outline: none;
		border: none;
		cursor: pointer;
		border-radius: 5px;
	}
	.submit-btn {
		padding: 8px;
		color: #fff;
		background: #26ae68;
		transition: background .2s ease;
		&:hover, &:focus{
			background: lighten(#26ae68, 6%);
		}
	}
	.close-modal {
		padding: 8px;
		color: #fff;
		background: #db4c3f;
		transition: background .2s ease;
		&:hover, &:focus{
			background: lighten(#db4c3f, 6%);
		}
	}
	.close-icon{
		cursor: pointer;
	}
}
</style>