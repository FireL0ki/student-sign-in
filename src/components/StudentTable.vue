<template>
    
    <div>
        <!-- Template/HTML here -->

        <div class="card student-list m-2 p-2">
            <h4 class="card-title">Student List</h4>
            <div id="student-table">
                <table class="table">
                    <tr>
                        <th>Name</th>
                        <th>StarID</th>
                        <th>Present?</th>
                    </tr>

                    <tr v-for="student in students" v-bind:key="student.starID" v-bind:class=" { present: student.present, absent: !student.present } ">
                        <!-- student is the name of the vue data property (in the app) -->
                        <td>{{ student.name }}</td>
                        <td>{{ student.starID }}</td>
                        <td>
                            <input type="checkbox" v-model="student.present" v-on:change="arrivedOrLeft(student)">
                        </td>
                    </tr>

                </table>
            </div>
        </div>

    </div>

</template>

<script>

export default {
    // create component here
    name: 'StudentTable',
    props: {
        students: Array
    },
    methods: {
        arrivedOrLeft() {
            // TODO emit message to parent
        }
    }
}
</script>


<style scoped>

</style>
