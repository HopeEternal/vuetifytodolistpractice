<template>
  <v-app id="inspire">
    <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col cols="12" sm="8" md="6">
            <v-card class="elevation-12">
              <v-toolbar color="primary" dark flat>
                <v-toolbar-title>To Do List</v-toolbar-title>
              </v-toolbar>
              <v-card-text>
                <v-list>
                  <v-subheader>Tasks</v-subheader>
                  <div v-for="(todo, index) in todos" :key="index">
                    <v-list-item>
                      <v-list-item-action>
                        <v-icon @click="todoComplete(index)">mdi-checkbox-blank-circle-outline</v-icon>
                      </v-list-item-action>
                      <v-list-item-content>
                        <v-list-item-title
                          @dblclick="todoEdit(index)"
                          v-model="todo.title"
                          v-if="!todo.editing"
                        >{{ todo.name }}</v-list-item-title>
                        <v-text-field
                          class="editable"
                          label="Edit Me"
                          name="editTodo"
                          append-icon="mdi-pencil"
                          type="text"
                          v-model="todo.title"
                          v-else
                        />
                      </v-list-item-content>
                    </v-list-item>

                    <v-divider></v-divider>
                  </div>
                </v-list>

                <v-form>
                  <v-text-field
                    label="Enter a task to add"
                    name="login"
                    prepend-icon="mdi-account-check"
                    type="text"
                    v-model="newTodo"
                  />
                </v-form>
              </v-card-text>
              <v-card-actions>
                <v-spacer />
                <v-btn color="primary" @click="addTodo()">Add</v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "TodoList",

  data: () => ({
    todos: [
      { name: "Cook", editing: false },
      { name: "Clean", editing: false },
      { name: "Code", editing: false }
    ],
    newTodo: ""
  }),
  methods: {
    addTodo() {
      if (!this.newTodo) {
        alert("Please enter a new task to add!");
      } else {
        this.todos.push({ name: this.newTodo });
        this.newTodo = "";
      }
    },
    todoComplete(index) {
      this.todos.splice(index, 1);
    },
    todoEdit(index) {
      console.log(this.todos[index]);
      this.todos[index].editing = true;
    }
  }
};
</script>


<style>
</style>