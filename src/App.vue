<template>
  <div class="container">
    <div id="app" class>
      <div class="long">
        <div class="spa">
          <h1 v-on:click="makeSum">{{ title }}</h1>
          <HelloWorld msg="This is my TODO APP" />
          <input
            type="tet"
            placeholder="Enter things here"
            v-on:keyup.enter="addTolist"
            class="paperInputs2"
          />
          <button v-on:click="addTolist">ADD</button>
          <ul class="flex">
            <draggable>
              <li v-for="todo in todos" :key="todo">
                <!-- <label> -->
                <input
                  type="checkbox"
                  class="checkbox"
                  @click="check(todo)"
                  :checked="todo.done"
                  style="width:30px"
                />
                <div class="test">
                  <del v-if="todo.done">{{ todo.text }}</del>
                  <span v-else>{{ todo.text }}</span>
                </div>
                <button class="btn-small" v-on:click="removeTolist(todo.id)">
                  Del
                </button>
              </li>
            </draggable>
          </ul>
        </div>
      </div>
      <br />
      <Mine msg="Later Additions" />
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Mine from "./components/mine.vue";
import draggable from "vuedraggable";
export default {
  name: "app",
  components: {
    HelloWorld,
    Mine,
    draggable,
  },
  // el: "#app",

  data() {
    return {
      title: "Vue Todo app, Test",
      disableButton: [{ disableButton: true }],
      todos: [
        { text: "todo-1", done: false, id: 1 },
        { text: "dragging-1", done: false, id: 2 },
        { text: "testing-2", done: false, id: 3 },
      ],
    };
  },
  methods: {
    addTolist(event) {
      var text = event.target.value;
      if (text.length > 0) {
        this.todos.push({ text, done: false, id: [0] });
        text = "";
      } else {
        alert("Input sometiinngs");
      }
      console.log(this.todos);
    },
    removeTolist(id) {
      this.todos = this.todos.filter((todo) => todo.id !== id);
      console.log(this.todos);
    },
    check(todo) {
      todo.done = !todo.done;
    },
    makeSum() {
      alert("Test complete");
    },
  },
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
/* .long {
  border-style: solid;
  border-radius: 20px;
  animation: mything 1s alternate linear infinite;
} */
li {
  list-style-type: none;
  margin: 8px;
}
.spa {
  margin-left: 12%;
}
/* @keyframes mything {
  from {
    border-color: red orange rgb(150, 150, 46) green;
  }
  to {
    border-color: blue indigo violet pink;
  }
} */
</style>
