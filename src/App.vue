<template>
  <div class="todo">
    <h2>{{ logo }}</h2>
    <div class="wrapper">
      <app-input :value="name" @input="onNameChanged"></app-input>
      <div class="wrap">
        <app-button @click="onClick" text="Добавить"></app-button>
        <app-sorted @sorted="toggleSort" :isAsc="isAsc"></app-sorted>
      </div>
    </div>
    <todo-list
      :list="currentPageTodos"
      @delete="onDelete"
      @edit="onEdit"
      @toggleDone="onToggleDone"
    ></todo-list>
    <p>
      <button v-for="(page, i) in pages" :key="i" @click="setCurrentPage(page)">{{ page + 1 }}</button>
    </p>
    <edit-modal v-if="editingTodo" @onEdit="onEditConfirm" :todo="editingTodo"></edit-modal>
  </div>
</template>

<script>
import AppInput from "./AppInput.vue";
import AppButton from "./AppButton.vue";
import TodoList from "./TodoList.vue";
import AppCheckbox from "./AppCheckbox.vue";
import AppSorted from "./AppSorted.vue";
import EditModal from "./EditModal.vue";

export default {
  data() {
    return {
      name: "",
      logo: "Todo List",
      todos: [],
      currentPage: 0,
      elementsPerPage: 3,
      isAsc: true,
      editingTodo: null
    };
  },
  components: {
    AppInput,
    AppButton,
    TodoList,
    AppCheckbox,
    AppSorted,
    EditModal
  },
  computed: {
    sortedTodos() {
      const todos = this.todos.slice();
      return todos.sort((first, second) => {
        if (!this.isAsc) {
          return second.createdAt - first.createdAt;
        } else {
          return first.createdAt - second.createdAt;
        }
      });
    },
    pages() {
      const pages = [];
      const totalPages = Math.ceil(this.todos.length / this.elementsPerPage);

      for (let i = 0; i < totalPages; i++) {
        pages.push(i);
      }

      return pages;
    },
    currentPageTodos() {
      const startIdx = this.currentPage * this.elementsPerPage;
      const endIdx = startIdx + this.elementsPerPage;

      return this.sortedTodos.slice(startIdx, endIdx);
    }
  },
  methods: {
    onNameChanged(name) {
      this.name = name;
    },
    onClick() {
      const todo = {
        name: this.name,
        isDone: false,
        createdAt: new Date().getTime()
      };
      this.todos.push(todo);
      this.name = "";
    },
    onDelete(todo) {
      const index = this.todos.indexOf(todo);
      this.todos.splice(index, 1);
    },
    setCurrentPage(page) {
      this.currentPage = page;
    },
    toggleSort() {
      this.isAsc = !this.isAsc;
    },
    onEdit(todo) {
      this.editingTodo = todo;
    },
    onToggleDone(createdAt) {
      const todo = this.todos.find(todo => todo.createdAt === createdAt);
      todo.isDone = !todo.isDone;
    },
    onEditConfirm(name) {
      const todo = this.todos.find(
        todo => todo.createdAt === this.editingTodo.createdAt
      );
      todo.name = name;
      this.editingTodo = null;
    }
  }
};
</script>

<style scoped>
.todo {
  border-radius: 10px;
  max-width: 800px;
  border: 1px solid black;
  margin: 0 auto;
  padding: 10px;
  background-color: rgb(243, 207, 174);
  position: relative;
}

h2 {
  text-align: center;
  font-family: "Montserrat", sans-serif;
}

.wrapper {
  display: flex;
  justify-content: space-between;
}

.wrap {
  display: flex;
  width: 100%;
}

p {
  text-align: center;
}

button {
  margin-right: 5px;
}

@media screen and (max-width: 670px){
  .todo {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  .wrapper {
    display: flex;
    flex-direction: column;
  }
  
  .wrap {
    margin-top: 20px;
    margin-bottom: 30px;
  }
}
</style>