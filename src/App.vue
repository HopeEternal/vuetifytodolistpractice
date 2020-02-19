<template>
  <v-app>
    <v-app-bar app color="indigo" dark>
      <div class="d-flex align-center text-center">
        <v-icon large>mdi-checkbox-multiple-marked-circle-outline</v-icon>
        <h1 class="font-weight-light text-right">Just Do It!</h1>
      </div>
    </v-app-bar>

    <v-content>
      <TodoList />
    </v-content>
  </v-app>
</template>

<script>
import TodoList from "./components/TodoList";

export default {
  name: "App",

  components: {
    TodoList
  },

  data: () => ({
    //
  })
};
</script>
