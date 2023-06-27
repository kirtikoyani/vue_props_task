<template>
    <div class="studentsList">
        <h2>{{ subject.name }}</h2>
        <p>{{ subject.description }}</p>
        <stud-pe-m v-for="student in subject.students" :key="student" />
    </div>
    </template>

    <script>
import StudPeM from './studPeM.vue';

    export default {
        inject: ['subjects'],
        components: {
                StudPeM
        },
        computed: {
            subject() {
                const subjects = this.subjects();
                return subjects.find(s => s.id === this.$vnode.key);
            }
        },
    };
    </script>

    <style>
    .subjectList {
        display: flex;
        justify-content: center;
        width: calc(90% + 44px);
        gap: 20px;
        margin: 0 auto;
    }
    </style>
