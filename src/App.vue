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
        <button v-on:click="addTolist">ADD</button>
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
            <div class="test">
              <del v-if="todo.done">{{ todo.text }}</del>
              <span v-else>{{ todo.text }}</span>
            </div>
            <button class="btn-small" v-on:click="removeTolist(todo.id)">Del</button>
          </li>
        </ul>
      </div>
      <Mine msg="Later Additions" />
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
  // el: "#app",

  data() {
    return {
      title: "Vue Todo app, Test",
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
      this.todos.push({ text, done: false, id: [0] });
      text = "";

      console.log(this.todos);
    },
    removeTolist(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
      console.log(this.todos);
    },
    check(todo) {
      todo.done = !todo.done;
    },
    makeSum() {
      alert("Test complete");
    }
  }
};
</script>

<style>
body {
  background: aquamarine;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 250px;
}
li {
  list-style: none;
  margin: 8px;
}
</style>
