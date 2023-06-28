<template>
<div>
    <h1 class="title">Provide Inject Method2</h1>
    <div class="subjectList">
        <sub-pe-m v-for="subject in subjects" :key="subject.id" />
    </div>
</div>
</template>

<script>
import SubPeM from './subPeM.vue';

export default {
    components: {
        SubPeM
    },
    data() {
        return {
            subjects: [{
                    id: 3,
                    name: 'English',
                    description: 'The English language is an Indo-European language',
                    students: [11, 14, 12]
                },
                {
                    id: 4,
                    name: 'Hindi',
                    description: 'Hindi has been described as a standardised and Sanskritised',
                    students: [11, 12, 13]
                },
                {
                    id: 5,
                    name: 'Gujrati',
                    description: 'Gujarati is an Indo-Aryan language native to Gujarat',
                    students: [11, 13, 14]
                }
            ],
            students: [{
                    id: 11,
                    rollNo: '011',
                    name: 'Kirti Koyani'
                },
                {
                    id: 12,
                    rollNo: '012',
                    name: 'Dhrupal Savaliya'
                },
                {
                    id: 13,
                    rollNo: '013',
                    name: 'Adarsh Parmar'
                },
                {
                    id: 14,
                    rollNo: '014',
                    name: 'Amish Joshi'
                }
            ]
        };
    },
    provide() {
        return {
            subjects: () => this.subjects,
            students: () => this.students,
            updateStudentName: this.updateStudentName
        };
    },
    methods: {
        updateStudentName(updatedStudent) {
            const {
                id,
                name
            } = updatedStudent;
            const student = this.students.find(student => student.id === id);
            if (student) {
                this.students.splice(name, 1, updatedStudent);
            }
        }
    }
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

.title {
    background: bisque;
    width: calc(90% + 6px);
    border: 1px solid;
    margin: 20px auto;
    padding: 20px;
}
</style>
