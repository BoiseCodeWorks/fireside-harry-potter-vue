<template>
  <div class="student col-3 card">
    <h2>{{s.name}}</h2>
    <button @click="addPoints">add points</button>
  </div>
</template>

<script>
  export default {
    name: 'student',
    props: ['s'],
    data() {
      return {

      }
    },
    computed: {},
    methods: {
      addPoints() {
        this.$store.dispatch('addPoints', this.s.house)
      }
    }
  }

</script>

<style>


</style>