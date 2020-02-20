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
                <p v-for="(todo, index) in todos" :key="index">{{ todo }}</p>
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
    todos: ["Cook", "Clean", "Code"],
    newTodo: ""
  }),
  methods: {
    addTodo() {
      this.todos.push(this.newTodo);
      this.newTodo = "";
    }
  }
};
</script>
