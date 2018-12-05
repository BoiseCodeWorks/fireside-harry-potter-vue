<template>
  <div class="home container">
    <div class="row mb-5 pb-5">
      <div class="col">
        <img class="left" alt="Vue logo" src="../assets/logo.png">
        <img class="right" alt="Vue logo" src="../assets/logo.png">
        <h2 class="title">itchcraft and Wizardry</h2>
      </div>
    </div>
    <houses class="mt-5 pt-5"></houses>
    <div class="row">
      <student v-for="student in students" :key="student._id" :s="student"></student>
    </div>
  </div>
</template>

<script>
  import Student from '@/components/Student.vue'
  import Houses from '@/components/Houses.vue'

  export default {
    name: 'home',
    //same as running a method on instantiation of constructor in controller or service with vanilla
    mounted() {
      this.$store.dispatch('getStudents')
    },
    computed: {
      hufflepuff() {
        return this.$store.state.students.filter(s => s.house == 'Hufflepuff')
      },
      students() {
        return this.$store.state.students.filter(c => c.role == 'student')
      }
    },
    components: {
      Student,
      Houses
    }
  }
</script>

<style>
  .home {
    position: relative;
  }

  .left {
    transform: rotate(350deg);
    position: absolute;
    top: -3vh;
  }

  .right {
    transform: rotate(10deg);
    position: absolute;
    top: -3vh;
    left: 7vw;
  }

  .title {
    position: absolute;
    left: 18vw;
    top: 12vh;
  }
</style>