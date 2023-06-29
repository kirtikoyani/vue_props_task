<template>
<div class="subject-with-student">
    <div class="student-card">
        {{ student }}
    </div>
</div>
</template>


<script>
  import {EventBus} from '../../eventBus';

export default {
    data() {
        return {
            student:[],
        };
    },
    props:['studentId','hi'],
    mounted() {
      console.log(this.studentId,this.hi)
      EventBus.$on('students', s=>{
        this.student=s;return this.student
      });
    },
    methods: {
        students(s) {
          this.student=s;
          console.log(s)
        }
    }
};
</script>


<style>
/* Styles for StudentEventBus component */
</style>
