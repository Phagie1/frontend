<template>
    <div>
        <b-modal id="editStudentModal" title="Edit Student" ok-title="Save Student" @ok="onSubmit">
            <form action="#">
                <b-form-group label="Name" label-for="name">
                <b-form-input id="name" v-model="student.name" trim></b-form-input>
                </b-form-group>student

                <b-form-group label="Age" label-for="age">
                <b-form-input id="age" v-model="student.age" trim></b-form-input>
                </b-form-group>


                <b-form-group label="Address" label-for="address">
                <b-form-input id="address" v-model="student.address" trim></b-form-input>
                </b-form-group>


                <b-form-group label="Contact" label-for="contact">
                <b-form-select v-model="student.contact" :options="options"></b-form-select>
                </b-form-group>
            </form>
        </b-modal>
    </div>
</template>

<script>
export default {
    props: {
        student: {}
    },
    data() {
        return {
            options: [
                {value: 'programmer', text: 'programmer'},
                {value: 'designer', text: 'designer'},
               
            ]
        }
    },
    methods: {
        async onSubmit() {
            this.$axios.put('/api/students/' + this.student.id, this.student)
            .then((res)=>{
                if(res.status==202) {
                    alert('Edit successful!')
                }
            })
            .catch((err)=>{
                alert(err.message)
            })
        }
    }
}
</script>