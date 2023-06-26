<template>
<div>
    <h1 class="title">Subjects</h1>
    <div class="subjectList">
        <the-subject v-for="subject in subjects" :key="subject.id" :subject="subject" @name-updat="getName" />
    </div>
</div>
</template>

<script>
import TheSubject from './TheSubject.vue';

export default {
    components: {
        TheSubject,
    },
    data() {
        return {
            subjects: [{
                    id: 1,
                    name: 'Physics',
                    description: 'Physics is the science of matter',
                    students: [{
                            id: 1,
                            rollNo: '001',
                            name: 'Kirti Koyani'
                        },
                        {
                            id: 2,
                            rollNo: '002',
                            name: 'Dhrupal Savaliya'
                        },
                        {
                            id: 3,
                            rollNo: '003',
                            name: 'Adarsh Parmar '
                        },
                    ],
                },
                {
                    id: 2,
                    name: 'Chemistry',
                    description: 'Branch of science that deals with atoms',
                    students: [{
                            id: 1,
                            rollNo: '001',
                            name: 'Kirti Koyani'
                        },
                        {
                            id: 2,
                            rollNo: '002',
                            name: 'Dhrupal Savaliya'
                        },
                        {
                            id: 4,
                            rollNo: '004',
                            name: 'Amish Joshi'
                        }
                    ],
                },
                {
                    id: 3,
                    name: 'Maths',
                    description: 'Maths is a subject that deals with numbers',
                    students: [{
                            id: 1,
                            rollNo: '001',
                            name: 'Kirti Koyani'
                        },
                        {
                            id: 4,
                            rollNo: '004',
                            name: 'Amish Joshi'
                        },
                        {
                            id: 3,
                            rollNo: '003',
                            name: 'Adarsh Parmar '
                        }
                    ],
                },
            ],
        };
    },
    methods: {
        getName(updatedStudent) {
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
    border: 1px solid;
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
