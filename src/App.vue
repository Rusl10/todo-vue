<template>
  <div id="app">
    <div class="todo">
      <div class="todo__header">
        <h4>Список задач</h4> 
      </div> 
      <v-task-field 
      @addTask="addTaskToList"
      />
      <div class="todo__list">
        <v-list-item 
          v-for="(task, index) in list" 
          :task="task" 
          :key="index"
          @checkTask="checkTask(index)"
          @deleteTask="deleteTask(index)"
        />
      </div>
    </div>
  </div>
</template>

<script>
import vTaskField from './components/v-task-field'
import vListItem from './components/v-list-item'
import axios from 'axios'
export default {
  name: 'App',
  data(){
    return {
      list: []
    }
  },
  methods: {
    checkTask(index){
      this.list[index].checked = !this.list[index].checked
    },
    deleteTask(index){
      this.list.splice(index, 1)
    },
    addTaskToList(task){
      this.list.unshift({
        checked: false,
        title: task
      })
    }
  },
  mounted(){
    axios({
      method: 'get',
      url: 'http://localhost:3000/list'
    })
    .then((response) => {
      this.list = response.data

    })
    .catch((error) =>{
      console.log('error', error);
      return error
    })
  },
  components: {
    vTaskField,
    vListItem
  }
}
</script>

<style lang="scss">
body{
  background-color: #fafafa;
}
#app {
  font-family: Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.todo{
  position: absolute;
  left: 50%;
  top: 50%;
  width: 530px;
  height: 500px;
  border-radius: 6px;
  transform: translate(-50%, -50%);
  background-color: #fff;
  box-shadow: 0 9px 24px rgba(0, 0, 0, .01);
  overflow: hidden;
  border: 1px solid #ebebeb;
  &__header{
    background-color: #db4c3f;
    padding: 20px 30px;
    h4{
      color: #fff;
      font-size: 22px;
      font-weight: 500;
    }
  } 

  &__add-field{
    display: flex;
    border-bottom: 1px solid #f4f4f4;

    input{
      border: 0;
      font-size: 16px;
      padding: 20px;
      flex: 1;
      outline: none;
      &::-webkit-input-placeholder{
        color: #bfbfbf;
        opacity: 1;
      }
        
      &::-moz-input-placeholder{
        color: #bfbfbf;
        opacity: 1;

      }
      &:-moz-input-placeholder{
        color: #bfbfbf;
        opacity: 1  ;

      }
      &::-ms-input-placeholder{
        color: #bfbfbf;

      }
    }

    &-button{
      display: flex;
      align-items: center;
      justify-content: center;
      width: 65px;
      height: 65px;
      outline: none;
      border: 0;
      color: #bfbfbf;
      background-color: transparent;
      cursor: pointer;
      &:hover {
        background-color: #fbfbfb;
        color: #202020;
      }
    }
  } 
  &__list{
    &-item{
      $self: &;
      display: flex;
      align-items: center;
      padding: 20px 30px;
      border-bottom: 1px solid #f4f4f4;
      &--completed{

          #{$self}-check{
            .material-icons{
              display: inline;
            }
          }
          #{$self}-check,
          #{$self}-check:hover {
            background-color: #fff;
          
          }
          p {
            text-decoration: line-through;
          }
      }
      &-check{
        display: flex;
        align-items: center;
        justify-content: center;
        border: 2px solid #db4c3f;
        border-radius: 30px;
        height: 24px;
        width: 24px;
        margin-right: 15px;
        cursor: pointer;

        
        &:hover{
          background-color: #f8e0de;
        }
        .material-icons{
          color: #db4c3f;
          font-size: 33px;
          display: none;
        }
      }

      p {
        font-size: 18px;
        flex: 1;
      }
      &-remove{
        color: #bfbfbf;
        cursor: pointer;
        block-size: 23px;
        &:hover{
          color: #202020;
        }
      }
    }
  }
}
</style>
