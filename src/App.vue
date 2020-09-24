<template>
  <nav class="navbar navbar-dark bg-primary mb-4">
    <span class="navbar-brand mx-auto">Tasks Today: {{ tasks }}</span>
  </nav>
  <div class=" container input-group input-group-lg">
    <input
      v-model="msg"
      type="text"
      class="form-control"
      aria-label="Large"
      aria-describedby="inputGroup-sizing-sm"
    />
    <div class="input-group-prepend">
      <button @click="inc" class="input-group-text btn btn-primary">Add</button>
    </div>
  </div>
  <div class="mt-1 container">
    <table class="mx-auto table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Task</th>
          <th scope="col">Edit / Delet</th>
        </tr>
      </thead>
      <tbody v-for="(item, index) in todo" :key="item">
        <tr>
          <th scope="row">{{ index + 1 }}</th>
          <td>{{ item }}</td>
          <td>
            <button @click="rem(index)" class="btn btn-danger btn-sm">
              Remove
            </button>
            <button @click="edit(index)" class="btn btn-primary btn-sm">
              Edit
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "App",
  data: function() {
    return {
      msg: "ADD",
      todo: ["Add Something"],
      tasks: 0
    };
  },
  methods: {
    inc: function() {
      this.todo.push(this.msg);
      this.msg = "";
      this.tasks = this.todo.length;
    },
    rem: function(index) {
      this.todo.splice(index);
      this.tasks = this.todo.length;
    },
    edit: function(index) {
      this.todo[index] = prompt("what do you want it to be");
    }
  },
  created: function() {
    this.tasks = this.todo.length;
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
