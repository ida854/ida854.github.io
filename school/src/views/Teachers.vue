<template>
  <div>
    <b-table striped hover :items="teachers">
    <template v-slot:cell(name)="data">
        <router-link :to="`/teachers/${data.index}`">{{ data.value }}</router-link>
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
    teachers () {
      return this.$store.state.teachers
    }
  }
}
</script>
