<template>
  <div id="app">

    <new-student-form v-on:student-added="newStudentAdded"></new-student-form>
    <student-table 
      v-bind:students="students"
      v-on:student-arrived-or-left="studentArrivedOrLeft"
      v-on:delete-student="studentDeleted">
    </student-table>
    <student-message v-bind:student="mostRecentStudent"></student-message>

  </div>
</template>

<script>
import NewStudentForm from './components/NewStudentForm.vue'
import StudentMessage from './components/StudentMessage.vue'
import StudentTable from './components/StudentTable.vue'

export default {
  name: 'App',  
  data() {
    return {
      students: [
        { name: 'Example', 'starID': 'aa1234aa', present: true },
        { name: 'Test', 'starID': 'zz3452uu', present: false },
      ],
      mostRecentStudent: {}
    }
  },
  components: {
    NewStudentForm,
    StudentMessage,
    StudentTable,
  },

  methods: {
    newStudentAdded(student) {
        this.students.push(student)
        this.students.sort(function(s1, s2) {
          return s1.name.toLowerCase() < s2.name.toLowerCase() ? -1 : 1
        })
    },
    studentArrivedOrLeft() {
      // find student in array of students
      // update present attribute

      let updateStudent = this.students.find( function(s) {
        if (s.name === student.name && s.starID === student.starID) {
          // this is the student to update
          return true
        }
      })

      if (updateStudent) {
        updateStudent.present = present
        this.mostRecentStudent = updateStudent
      }
    }
  }
}
</script>

<style>

@import "https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
