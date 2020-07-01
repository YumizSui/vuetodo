<template>
  <div>
    <h1>タスクタスク</h1>
    <label>
      タスク内容
      <input type="text" v-model="newTask" />
    </label>
    <label>
      締め切り
      <input type="text" v-model="newDeadLine" />
    </label>
    <button @click="addTask(ind)">追加</button>
    <table class="table justifiy-content-center">
      <th width="100">進捗</th>
      <th width="200">タスク内容</th>
      <th width="100">期限</th>
      <th width="100">完了</th>
      <th width="100">削除</th>
      <tr v-for="(task, ind) in tasks" :key="task.id">
        <td v-if="task.status == false">
          まだ
        </td>
        <td v-else>ヨシ</td>
        <td v-if="task.deadline == ''">締め切なし</td>
        <td v-else>{{ task.deadline.toLocaleString() }}</td>
        <td>
          <button @click="task.status = true">完了</button>
        </td>
        <td>
          <button @click="deleteTask(ind)">削除</button>
        </td>
        <td>{{ ind }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "ItemList",
  data() {
    return {
      tasks: [
        {
          id: 0,
          content: "todoをやる",
          deadline: "",
          status: false,
        },
        {
          id: 1,
          content: "課題をやれ",
          deadline: "2020/5/5",
          status: true,
        },
      ],
      newTask: "",
      newDeadLine: "",
    };
  },
  methods: {
    addTask(id) {
      this.tasks.push({
        id: id,
        content: this.newTask,
        deadline: this.newDeadLine,
        status: false,
      });
    },
    deleteTask(id) {
      this.tasks.splice(id, 1);
    },
  },
};
</script>

<style></style>
