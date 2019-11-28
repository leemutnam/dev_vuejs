<template>
  <div class="iframe">
    <p>iframe 태그 영역</p>
    <div v-if="one_result">
      <p>RESULT</p>
      <table>
        <tr>
          <th>id</th>
          <th>employee_name</th>
          <th>employee_salary</th>
          <th>employee_age</th>
        </tr>
        <tr>
          <td>{{one_result.data.id}}</td>
          <td>{{one_result.data.employee_name}}</td>
          <td>{{one_result.data.employee_salary}}</td>
          <td>{{one_result.data.employee_age}}</td>
        </tr>
      </table>
    </div>
    <input type="text" v-model="name">
    <button @click="finder(name, result)">이름 검색</button>
    <p v-for="(re, index) in result" v-bind:key="index">{{re.employee_name}}</p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      result: null,
      one_result: null,
      name: null
    }
  },
  methods: {
    finder: function (word, list) {
      let newMan = list.filter(a => word === a.employee_name)
      if (newMan.length === 0) {
        this.one_result = ''
        return ''
      }
      axios.get(`http://dummy.restapiexample.com/api/v1/employee/${newMan[0].id}`)
        .then((res) => {
          this.one_result = res
        })
        .catch((err) => {
          console.log(err)
        })
    }
  },
  computed: {},
  created () {
    axios.get('http://dummy.restapiexample.com/api/v1/employees')
      .then((res) => {
        this.result = res.data
      })
      .catch((err) => {
        console.log(err)
      })
  }
}
</script>

<style scoped>

</style>
