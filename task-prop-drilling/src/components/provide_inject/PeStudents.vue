<template>
<div class="subject-with-student">
    <div class="student-card">
        <h3>Roll No: {{ student().rollNo }}</h3>
        <h4>Name: {{ student().name }}</h4>
        <button class="btn" v-if="!isEditing" @click="editName">Edit Name</button>
        <div v-if="isEditing">
            <input class="input" type="text" id="fname" v-model="editedName" />
            <button class="btn-save" @click="saveName">Save</button>
            <button class="btn-cansal" @click="cancelEdit">Cancel</button>
        </div>
    </div>
</div>
</template>

<script>
export default {
    inject: ['subjects', 'updateStudentName'],
    data() {
        return {
            isEditing: false,
            editedName: this.student().name,
        };
    },
    created() {
        this.student()
    },
    methods: {
         student() {
            const subjects = this.subjects();
            const student = subjects.flatMap(subject => subject.students).find(student => student.id === this.$vnode.key);
            return student;
        },
        editName() {
            this.isEditing = true;
            this.editedName = this.student().name;
        },
        saveName() {
            const updatedStudent = {
                ...this.student(),
                name: this.editedName
            };
            this.isEditing = false;
            this.updateStudentName(updatedStudent);
        },
        cancelEdit() {
            this.isEditing = false;
            this.editedName = this.student().name;
        },
    }
};
</script>