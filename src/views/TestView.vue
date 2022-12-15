<template>
  <div class="test">
    <input type="text" v-model="inputName" />
    <button @click="clickHandler">Add name</button>
    <ul class="list">
      <li v-for="(name, i) in names" :key="i">{{ name }}</li>
    </ul>
    <button :title="title">Hover over me</button>
    <div>
      <h3>All Tasks:</h3>
      <ul>
        <li v-for="task in tasks" :key="task.id" class="list-item">
          <p class="list-item__content">{{ task.text }}</p>
          <p>
            Is completed:
            <span :class="task.completed ? 'completed' : 'notCompleted'">{{
              task.completed
            }}</span>
          </p>
          <button @click="toggleTaskState(task)">Change complete state</button>
        </li>
      </ul>
      <h3>Complete Tasks:</h3>
      <ul>
        <li v-for="task in completeTasks" :key="task.id">
          {{ task.text }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "TestView",
  data: function () {
    return {
      names: ["John", "Jack", "Tom"],
      inputName: "",
      title: "Just a sample title",
      tasks: [
        {
          id: "639b85b45e102faf0772094c",
          text: "consequat ex ullamco veniam fugiat adipisicing nisi",
          completed: false,
        },
        {
          id: "639b85b4b05fa81f3233b4e6",
          text: "deserunt ad incididunt sunt proident in dolore",
          completed: true,
        },
        {
          id: "639b85b4c985fdad01f77d07",
          text: "reprehenderit cillum tempor aliqua adipisicing qui esse",
          completed: false,
        },
        {
          id: "639b85b4ffa6d3962f397c0c",
          text: "aliqua laborum nostrud magna Lorem fugiat ex",
          completed: true,
        },
        {
          id: "639b85b49aa7d78d0b36e484",
          text: "adipisicing nostrud minim veniam ex id nostrud",
          completed: false,
        },
        {
          id: "639b85b400694fe5bb336420",
          text: "sunt est cillum Lorem commodo adipisicing magna",
          completed: true,
        },
      ],
    };
  },
  computed: {
    completeTasks() {
      return this.tasks.filter((task) => task.completed);
    },
  },
  methods: {
    clickHandler() {
      this.names.push(this.inputName);
      this.inputName = "";
    },
    toggleTaskState(task) {
      task.completed = !task.completed;
    },
  },
};
</script>

<style scoped lang="scss">
.test {
  width: 30rem;
  margin-inline: auto;

  ul {
    text-align: left;
    list-style-type: none;

    .list-item {
      border: 2px solid #d1d1d1;
      padding: 0.5rem;
      margin-bottom: 0.75rem;

      &__content {
        font-weight: 600;
      }

      .completed {
        color: blueviolet;
      }

      .notCompleted {
        color: red;
      }
    }
  }
}
</style>
