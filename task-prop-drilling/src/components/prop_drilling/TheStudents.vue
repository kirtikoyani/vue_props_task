<template>
<div class="subject-with-student">
    <div class="subject-details">
        <h3>Subject: {{ subject.name }}</h3>
        <h5>Description: {{ subject.description }}</h5>
    </div>
    <div class="student-card">
        <h3>Roll No: {{ student.rollNo }}</h3>
        <h4>Name: {{ student.name }}</h4>
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
    props: {
        subject: {
            type: Object,
            requred: true
        },
        student: {
            type: Object,
            requred: true
        }
    },
    emits: ["name-updated"],
    data() {
        return {
            isEditing: false,
            editedName: this.student.name,
        };
    },
    methods: {
        editName() {
            this.isEditing = true;
        },
        saveName() {
            const updatedStudent = {
                ...this.student,
                name: this.editedName
            };
            this.isEditing = false;
            this.$emit('name-updated', updatedStudent);
        },
        cancelEdit() {
            this.isEditing = false;
            this.editedName = this.student.name
        },
    }
};
</script>

<style>
.student-card {
    background: white;
    padding: 20px;
    margin: 25px;
    border: 1px solid;
    border-radius: 20px;
}

.btn,
.input,
.btn-save,
.btn-cansal {
    padding: 10px;
}

.btn {
    background: bisque;
}

.input {
    background: white;
}

.btn-save {
    background: gray;
}

.btn-cansal {
    background: red;
}

.subject-with-student {
    margin: 20px;
    background: bisque;
    text-align: left;
}

.subject-details {
    padding: 0px 30px;
}
</style>
