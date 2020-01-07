<template>
  <div>
  <h2 style="color: purple">Welcome To IT-Högskolan</h2>
  <h6>Add new Student/Teacher</h6>
  <button @click= "toggle" >Toggle Form</button>
  <form style= "padding-bottom: 5%" @submit.prevent= "submitHandler" v-if="show">
  Name:<br>
<input v-model="formData.name" type="text" /> <br>

Last Name:<br>
<input v-model="formData.family" type="text" /> <br>

E-postadress:<br>
<input v-model="formData.email" type="email" /> <br>

Course:<br>
<input v-model="formData.kurs" type="text" /> <br>

Category:<br>
<select v-model="formData.cat">
<option  value="teachers">teachers</option>
<option value="students">students</option>
</select>
<button type="submit"  style= "background-color: green">Submit</button>
</form>
</div>
</template>
<script>
import { mapActions } from 'vuex'
export default {
  data () {
    return {
      show: false,
      formData: {
        name: '',
        family: '',
        email: '',
        kurs: '',
        cat: null
      }
    }
  },
  methods: {
    toggle () {
      this.show = !this.show
    },
    ...mapActions([
      'addUser'
    ]),
    submitHandler () {
      console.log('1')
      const { name, family, email, kurs, cat } = this.formData
      const payload = {
        cat,
        user: {
          name, family, email, kurs
        }
      }
      this.addUser(payload)
    }
  }
}
</script>
