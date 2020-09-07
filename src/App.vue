<template>
  <div id="app">
    <div class="todo">
      <div class="todo__header">
        <h4>Список задач</h4> 
      </div> 
      <div class="todo__add-field">
        <input type="text" placeholder="Введите текст задачи...">
        <button class="todo__add-field-button">
          <i class="material-icons">add</i>
        </button>
      </div>
      <div class="todo__list">
        <div class="todo__list-item">
          <div class="todo__list-item-check">
            <!-- <i class="material-icons">panorama_fish_eye</i> -->
            <i class="material-icons">check_circle</i>
          </div>
          <p>Изучить Vue.js</p>
          <div class="todo__list-item-remove">
            <i class="material-icons">delete_outline</i>
          </div>
        </div>
        <div class="todo__list-item todo__list-item--completed">
          <div class="todo__list-item-check">
            <i class="material-icons">check_circle</i>
            
          </div>
          <p>Изучить Vue.js</p>
          <div class="todo__list-item-remove">
            <i class="material-icons">delete_outline
</i>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
    
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
          font-size: 30px;
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
