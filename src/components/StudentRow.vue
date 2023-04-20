<template>
    
    <tr v-bind:class="{ present: student.present, absent: !student.present }">
        <td>{{ student.name }}</td>
        <td>{{ student.starID }}</td>
        <td>
        <input type="checkbox" v-on:change="arrivedOrLeft(student, $event.srcElement.checked)"></td>
        <td v-show="edit"><img v-on:click="deleteStudent" src="@/assets/delete.png"></td>
        </tr>

</template>

<script>
export default {
    name: 'studentRow',
    props: {
        Student: Object,
        edit: Boolean
    },
    methods: {
        arrivedOrLeft(student, present){
            this.$emit('arrived-or-left', student, present)
        },
        deleteStudent() {
            if (confirm(`Delete ${this.student.name}?`)) {
                this.$mit('delete-student', this.student)
            }
        }
    }
}

</script>

<style scoped>

.present {
    color: gray;
    font-style: italic;
}

.absent {
    color: black;
    font-weight: bold;
}

/* TODO set icon height*/
img{
    height: 25px;
}
</style>