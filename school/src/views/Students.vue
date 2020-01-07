<template>
  <div>
    <b-table striped hover :items="students">
    <template v-slot:cell(name)="data">
        <router-link :to="`/students/${data.index}`">{{ data.value }}</router-link>
    </template>
    </b-table>
  </div>
</template>
<script>
export default {
  data () {
    return {}
  },
  computed: {
    students () {
      return this.$store.state.students
    }
  }
}
</script>
