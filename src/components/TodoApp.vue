<template>
  <div class="todo">
    <form @submit.prevent="addTodo">
      <input type="text" v-model="namee" v-validate="'min:5'" name='todo'><br/>
      <transition name="alert-in" enter-active-class="animated flipInX" leave-active-class="animated flipOutX">
        <span class="alert" v-if="errors.has('todo')">{{ errors.first('todo') }}</span>
      </transition>
    </form>
    <ul>
      <transition-group enter-active-class="animated bounceInUp" leave-active-class="animated bounceOutLeft">  
        <li v-for="( data, index ) in todos" :key= index> 
          {{data.todo}} 
          <i class="fa fa-minus-circle" v-on:click="deleted(index)" ></i>
        </li>
      </transition-group>
    </ul>
    <p>Your list of todo's appear here...</p>
  </div>
</template>

<script>
export default {
  name: 'TodoApp',
  data:function(){
    return{
      namee: '',
      err: '',
      todos: [
        {
          "todo": "my first todo"
        },
        {
          "todo": "my second todo"
        }
      ]
    }
  },
  methods: {
    addTodo(){
      this.$validator.validateAll().then((result) =>{
        if(result){
          this.todos.push({todo: this.namee});
          this.namee = '';
          this.err = '';
        }
      })
      
    },
    deleted(index){
      this.todos.splice(index, 1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
@import "../../node_modules/animate.css/animate.css";
@import "https://use.fontawesome.com/releases/v5.5.0/css/all.css";
.todo{
  margin-top: 20px;
  width: 400px;
}
.todo input{
  width:390px;
  height: 40px;
  background-color: #222f3e;
  color:aliceblue;
  border:none;
  font-size: 14px;
  padding-left: 10px;
}
.todo input:focus{
  outline: none;
}
ul{
  margin:0;
  padding: 0;
}
li{
  list-style: none;
  padding: 20px 10px;
  background-color:#576574;
  color:white;
  margin-bottom: 3px;
  border-left:4px solid #34e7e4;
  font-size: 16px;
}
p{
  margin:0;
  padding: 20px 20px;
  border: 0.5px solid #ef5777;
}
.alert{
  font-size: 10px;
  background: #fdfe43;
  font-weight: bold;
  display: inline-block;
  padding: 5px;
  margin-top: -40px;
}
i{
  float: right;
}
</style>
