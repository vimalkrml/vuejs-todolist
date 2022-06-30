<script>
import TaskItems from "./TaskItems.vue";
import Notask from "./NoTasks.vue";
import TaskView from "./TaskView.vue";
import TaskAdd from "./TaskAdd.vue";
import TaskEdit from "./TaskEdit.vue";
export default {
  data() {
    return {
      status: false,
      tasks: [],
      task: {
        name: "",
        username: "",
        email: "",
      },
      task_preview_model: false,
      task_edit_model: false,
    };
  },
  methods: {
    async tasks_index() {
      console.log("Preview");
      await fetch("http://localhost:3004/users")
        .then((res) => res.json())
        .then((json) => {
          this.tasks = json;
          console.log(json);
        });
    },
    async tasks_remove(taskid) {
      console.log(taskid);
      const mutateData = this.tasks.filter((task) => task.id !== taskid);
      this.tasks = mutateData;
      await fetch("http://localhost:3004/users/" + taskid, { method: "DELETE" })
        .then((res) => res.json())
        .then((json) => console.log(json));
    },
    async tasks_show(taskid) {
      console.log(taskid);
      this.task_preview_model = true;
      await fetch("http://localhost:3004/users/" + taskid)
        .then((res) => res.json())
        .then((json) => {
          this.task = json;
          return;
        });
    },
    async tasks_add(e) {
      console.log("To-do added:", e);
      const data = new FormData(e.target);
      const value = Object.fromEntries(data.entries());
      const randonNum = Math.floor(Math.random() * 1000000000);
      value.id = randonNum;
      const mutatedata = [...this.tasks, { ...value }];
      this.tasks = mutatedata;
      const requestOptions = {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(value),
      };
      await fetch("http://localhost:3004/users", requestOptions).then((res) =>
        res.json()
      );
    },

    async task_edit(id) {
      this.task_edit_model = true;
      await fetch("http://localhost:3004/users/" + id)
        .then((res) => res.json())
        .then((json) => {
          this.task = json;
          return;
        });
    },

    async tasks_update(e, id) {
      console.log(id);
      const data = new FormData(e.target);
      const value = Object.fromEntries(data.entries());
      value.id = id;
      const mutateData = this.tasks.map((task) => {
        if (task.id === id) {
          return value;
        } else {
          return task;
        }
      });
      this.tasks = mutateData;
      this.task_edit_model = false;
      const requestOptions = {
        method: "PATCH",
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
        body: JSON.stringify(value),
      };

      await fetch("http://localhost:3004/users/" + id, requestOptions).then(
        (res) => res.json()
      );
    },
  },
  mounted() {
    this.tasks_index();
  },
  components: {
    TaskItems,
    Notask,
    TaskView,
    TaskAdd,
    TaskEdit,
  },
};
</script>

<template>
  <div>
    <task-add @onAdd="tasks_add"></task-add>
    <task-edit
      :show="task_edit_model"
      @onEdit="tasks_update"
      :item="task"
    ></task-edit>
    <task-view
      :show="task_preview_model"
      @onClose="this.task_preview_model = false"
    >
      <div
        class="
          border-2
          bg-orange-200
          py-3
          w-[40%]
          absolute
          top-[30%]
          right-[30%]
        "
      >
        <div class="flex justify-end mx-3">
          <button
            @click="task_preview_model = false"
            class="bg-orange-600 px-2"
          >
            x
          </button>
        </div>

        <div>
          <div class="text-center">ID-{{ task.id }}</div>
          <div class="text-center">Name-{{ task.name }}</div>
          <div class="text-center">Username-{{ task.username }}</div>
          <div class="text-center">Email-{{ task.email }}</div>
        </div>
      </div>
    </task-view>
    <div v-if="tasks.length > 0">
      <task-items
        @onDelete="tasks_remove"
        @onShow="tasks_show"
        :item="task"
        v-for="task in tasks"
        :key="task.id"
      >
        <div class="px-3">{{ task.name }}</div>
        <template #action>
          <div class="flex gap-4">
            <button
              @click="tasks_show(task.id)"
              class="
                text-white
                rounded-sm
                p-1
                bg-orange-300
                hover:bg-orange-600
              "
            >
              Preview
            </button>
            <button
              @click="task_edit(task.id)"
              class="text-white rounded-sm p-1 bg-blue-400 hover:bg-blue-600"
            >
              Edit
            </button>
            <button
              @click="tasks_remove(task.id)"
              class="text-white rounded-sm px-1 bg-gray-500 hover:bg-rose-600"
            >
              Delete
            </button>
          </div>
        </template>
      </task-items>
    </div>
    <notask v-else></notask>
  </div>
</template>