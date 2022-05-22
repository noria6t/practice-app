<template>
  <div class="container">
    <div>
      <h1 class="title">
        Practice-App
      </h1>
      <h2 class="subtitle">
        {{ subTitle }}
      </h2>
      <button @click="getSomething">
        タスク取得 
      </button>
      <ul v-for=" task in tasks" :key="task.id">
        <li style="text-align: left;">{{ task.title }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      subTitle: 'Practice-App is good service!!',
      tasks: []
    }
  },
  methods: {
    async getSomething() {
      const response = await this.$axios.$get('http://localhost:5000/api/v1/tasks')
      console.log(response)
      console.log(response.tasks)
      this.tasks = JSON.parse(response.tasks)
      console.log(this.tasks)
    }
  //   async getData() {
  // const res = await this.$axios('http://localhost:8080/').catch(err => {
  //   return err.response
  // })
// }
  },
}
</script>