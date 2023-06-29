<template>
    <div class="studentsList">
        <h2>{{ subject.name }}</h2>
        <p>{{ subject.description }}</p>
        <event-bus-students v-for="student in subject.students" :key="student.id" :student="student" :subject="subject" />
    </div>
    </template>

    <script>
import EventBusStudents from './EventBusStudents.vue';

    export default {
        props: {
            subject: {
                type: Object,
                requred: true
            }
        },
        emits: ["name-update"],
        components: {
            EventBusStudents,
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
