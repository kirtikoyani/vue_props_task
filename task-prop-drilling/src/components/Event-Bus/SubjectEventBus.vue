<template>
    <div class="studentsList">
      <h2>{{ subject.name }}</h2>
      <p>{{ subject.description }}</p>
      <!-- <div v-for="student in subject.students" :key="student"> -->
      <StudentEventBus :studentId="subject.students" hi="kirti" />
    <!-- </div> -->
    </div>
  </template>

  <script>
  import StudentEventBus from './StudentEventBus.vue';
  import {EventBus} from '../../eventBus';

  export default {
    components: {
      StudentEventBus
    },
    data() {
      return {
        subject: []
      };
    },
    created() {
      EventBus.$on('subjects', updatedSubjects => {
        this.subject = updatedSubjects.find(subject => subject.id === Number(this.$vnode.key));
      });
    }
  };
  </script>

  <style>
  /* Styles for SubjectEventBus component */
  </style>
