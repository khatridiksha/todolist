<template>
  <div class="flex-ac-dc-100 app-background">
    <div>
      <input
        type="text"
        class="input-style"
        placeholder="Write a todo....."
        v-model="newItem"
        @keyup.enter="addItem"
      />
      <div class="list">
        <p
          class="flex-ac-jsb border-bottom padding"
          v-for="(todo, index) in todos"
          :key="index"
        >
          <span :class="{ linethrough: isDone(todo) }">{{ todo }}</span>
          <span
            ><span
              class="btn done-btn"
              @click="markDone(todo)"
              >Done</span
            ><span class="delete-btn btn" @click="deleteItem(index)"
              >Delete</span
            ></span
          >
        </p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { doesNotMatch } from "assert";

// import Vue from 'vue'
export default {
  task: "todolist",
  data() {
    return {
      todos: ["A", "B", "C", "D"],
      newItem: '',
      doneItems: new Set(),
    };
  },
  methods: {
    deleteItem(index: any) {
      this.todos.splice(index, 1);
    },
    addItem() {
      if (this.newItem.trim() !== '') {
        this.todos.push(this.newItem);
        this.newItem = '';
      }
    },
    markDone(item: any) {
      if (this.isDone(item)) {
        this.doneItems.delete(item);
      } else {
        this.doneItems.add(item);
      }
    },
    isDone(item: any) {
      return this.doneItems.has(item);
    },
  },
};
</script>

<style scoped>
.flex-ac-dc-100 {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  width: 100vw;
}
.flex-ac-jsb {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.app-background {
  background: rgb(238, 174, 202);
  background: radial-gradient(
    circle,
    rgba(238, 174, 202, 1) 0%,
    rgba(148, 187, 233, 1) 100%
  );
}
.input-style {
  background-color: white;
  padding: 1.5em;
  border: 1px solid white;
  border-radius: 10px;
  width: 25vw;
}
.input-style:focus {
  outline: none;
}
.btn {
  padding: 0.5em 1em;
}

.delete-btn {
  background-color: red;
  color: white;
  border: 1px solid red;
  border-radius: 10px;
  margin-left: 0.2em;
}
.done-btn {
  background-color: white;
  color: green;
  border: 1px solid green;
  border-radius: 10px;
}
.task-completed-button {
  background-color: green;
  color: white;
  border: 1px solid green;
  border-radius: 10px;
}
.border-bottom {
  border-bottom: 1px dotted rgb(67, 67, 67);
}
.padding {
  padding: 0.5em 0.5em 0.9em 0.5em;
}
.list {
  background-color: white;
  border: 1px solid white;
  border-radius: 10px;
  padding: 0.5em;
  margin-top: 1em;
}
.linethrough {
  text-decoration: line-through;
}
</style>
