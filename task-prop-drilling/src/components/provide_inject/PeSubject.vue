<template>
<div class="studentsList">
    <h2>{{ subject.name }}</h2>
    <p>{{ subject.description }}</p>
    <pe-students v-for="student in subject.students" :key="student.id" :student="student" :subject="subject" />
</div>
</template>

<script>
import PeStudents from './PeStudents.vue';

export default {
    props: {
        subject: {
            type: Object,
            requred: true
        }
    },
    components: {
        PeStudents,
    }
};
</script>

<style>
.studentsList {
    display: flex;
    width: 100%;
    flex-direction: column;
    background: white;
}
</style>
