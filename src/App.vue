<template>
  <div id="app">

    <new-student-form v-on:student-added="newStudentAdded"></new-student-form>
    <student-table v-bind:students="students"></student-table>
    <student-message></student-message>

  </div>
</template>

<script>
import NewStudentForm from './components/NewStudentForm.vue'
import StudentMessage from './components/StudentMessage.vue'
import StudentTable from './components/StudentTable.vue'

export default {
  name: 'App',
  components: {
    NewStudentForm,
    StudentMessage,
    StudentTable,
  },
  data() {
    return {
      students: []
    }
  },
  methods: {
    newStudentAdded(student) {
        this.students.push(student)
        this.students.sort(function(s1, s2) {
          return s1.name.toLowerCase() < s2.name.toLowerCase() ? -1 : 1
        })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
