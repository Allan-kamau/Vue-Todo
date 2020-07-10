<template>
  <div class="container">
    <div id="app" class>
      <div class="long">
        <h1 v-on:click="makeSum">{{title}}</h1>
        <HelloWorld msg="This is my TODO APP" />
        <input
          type="text"
          placeholder="Enter things here"
          v-on:keyup.enter="addTolist"
          class="paperInputs2"
        />
        <button v-on:click="addTolist" v-bind:class="{disaled: disableButton}">ADD</button>
        <ul class="flex">
          <li v-for="todo in todos" :key="todo">
            <!-- <label> -->
            <input
              type="checkbox"
              class="checkbox"
              @click="check(todo)"
              :checked="todo.done"
              style="width:30px"
            />
            <span>&nbsp;</span>
            <!-- </label> -->
            <del v-if="todo.done">{{ todo.text }}</del>
            <span v-else>{{ todo.text }}</span>
            <button class="btn-small" v-on:click="removeTolist(todo.id)">Del</button>
          </li>
        </ul>
      </div>
      <Mine msg="creation of the component" />
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Mine from "./components/mine.vue";
export default {
  name: "app",
  components: {
    HelloWorld,
    Mine
  },


  data() {
    return {
      title: "Testing, testing",
      disableButton: [{ disableButton: true }],
      todos: [
        { text: "todo 1", done: false, id: 1 },
        { text: "todo 2", done: false, id: 2 }
      ]
    };
  },
  methods: {
    addTolist(event) {
      var text = event.target.value;
      text.length > 0;
      Date.now();
      this.todos.push({ text, done: false, id: [0] });
      text = "";

      console.log(this.todos);
    },
    removeTolist(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
      console.log("todos.text");
    },
    check(todo) {
      todo.done = !todo.done;
    },
    makeSum() {
      alert("something");
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 250px;
}
.long {
  border-style: solid;
  border-radius: 20px;
  border-width: 20px 20px thick;
  border-bottom-width: 20px;
  animation: mything 1s alternate linear infinite;
}
li {
  list-style: none;
  margin: 8px;
}
@keyframes mything {
  from {
    border-color: red orange rgb(150, 150, 46) green;
  }
  to {
    border-color: blue indigo violet pink;
  }
}
</style>
