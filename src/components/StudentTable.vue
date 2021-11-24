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
                            <input type="checkbox" v-bine:checked="student.present" v-on:change="arrivedOrLeft(student, $event.target.checked)">
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
    emits: ['student-arrived-or-left'],
    props: {
        students: Array
    },
    methods: {
        arrivedOrLeft(student, present) {
            // TODO emit message to parent
            this.$emit('student-arrived-or-left', student, present)
        }
    }
}
</script>


<style scoped>

.present {
    color: gray;
    font-style: italic;
}

.absent {
    color: black;
    font-weight: bold;
}



</style>
