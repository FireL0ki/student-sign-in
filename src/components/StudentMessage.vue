<template>
    
    <div v-if="student.name">
        <!-- Template/HTML here -->

        <div class="alert alert-success" v-if="mostRecentStudent.present">
            Welcome, {{ student.name }}
        </div>
        
    </div>

    <div class="alert alert-info" v-else>
        Goodbye, {{ student.name }}. See you later!
    </div>

</template>

<script>

export default {
    // create component here
    name: 'StudentMessage',
    props: {
        student: Object
    }
}
</script>


<style scoped>

</style>
