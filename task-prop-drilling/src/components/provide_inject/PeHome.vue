<template>
<div>
    <h1 class="title">Provide Inject</h1>
    <div class="subjectList">
        <pe-subject v-for="subject in subjects" :key="subject.id" :subject="subject" />
    </div>
</div>
</template>

<script>
import PeSubject from './PeSubject.vue';

export default {
    components: {
        PeSubject,
    },
    data() {
        return {
            subjects: [{
                    id: 3,
                    name: 'English',
                    description: 'The English language is an Indo-European language',
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
                            name: 'Adarsh Parmar '
                        },
                    ],
                },
                {
                    id: 4,
                    name: 'Hindi',
                    description: 'Hindi has been described as a standardised and Sanskritised',
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
                            id: 14,
                            rollNo: '014',
                            name: 'Amish Joshi'
                        }
                    ],
                },
                {
                    id: 5,
                    name: 'Gujrati',
                    description: 'Gujarati is an Indo-Aryan language native to the Gujarat',
                    students: [{
                            id: 11,
                            rollNo: '011',
                            name: 'Kirti Koyani'
                        },
                        {
                            id: 14,
                            rollNo: '014',
                            name: 'Amish Joshi'
                        },
                        {
                            id: 13,
                            rollNo: '013',
                            name: 'Adarsh Parmar '
                        }
                    ],
                },
            ],
        };
    },
    provide() {
        return {
            updateStudentName: this.updateStudentName,
        };
    },
    methods: {
        updateStudentName(updatedStudent) {
            const {
                id,
                name
            } = updatedStudent;
            this.subjects.forEach(subject => {
                const student = subject.students.find(student => student.id === id);
                if (student) {
                    student.name = name;
                }
            });
        }
    }
};
</script>

<style>
.subjectList {
    display: flex;
    justify-content: center;
    width: calc(90% + 44px);
    gap:20px;
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
