<template>
<div class="studentsList">
    <h2>{{ subject.name }}</h2>
    <p>{{ subject.description }}</p>
    <the-students v-for="student in subject.students" :key="student.id" :student="student" :subject="subject" @name-updated="getmethod" />
</div>
</template>

<script>
import TheStudents from './TheStudents.vue';

export default {
    props: {
        subject: {
            type: Object,
            requred: true
        }
    },
    emits: ["name-update"],
    components: {
        TheStudents,
    },
    methods: {
        getmethod(updatedStudent) {
            this.$emit('name-updat', updatedStudent)
        },
    }
};
</script>

<style>
.studentsList {
    display: flex;
    width: 100%;
    flex-direction: column;
    background: white;
    border: 1px solid;
}
</style>
