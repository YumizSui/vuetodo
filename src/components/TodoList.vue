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
        <td v-if="task.status == false">まだ</td>
        <td v-else>ヨシ</td>
        <td v>{{ task.content }}</td>
        <td v-if="task.deadline == ''">締め切なし</td>
        <td v-else>{{ task.deadline }}</td>
        <td>
          <button @click="task.status = true">完了</button>
        </td>
        <td>
          <button @click="deleteTask(ind)">削除</button>
        </td>
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
          content: "todoをつくる",
          deadline: "",
          status: false
        },
        {
          id: 1,
          content: "人工知能課題",
          deadline: "2020/7/14",
          status: false
        },
        {
          id: 2,
          content: "離散構造",
          deadline: "2020/7/27",
          status: false
        },
        {
          id: 3,
          content: "コンパイラ構成",
          deadline: "2020/7/17",
          status: false
        }
      ],
      newTask: "",
      newDeadLine: ""
    };
  },
  methods: {
    addTask(id) {
      this.tasks.push({
        id: id,
        content: this.newTask,
        deadline: this.newDeadLine,
        status: false
      });
    },
    deleteTask(id) {
      this.tasks.splice(id, 1);
    }
  }
};
</script>

<style></style>
