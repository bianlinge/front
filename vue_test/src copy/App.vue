<template>
<div>
  <Student nickname="zhangsan" sex="male" :IDCard="61212219920223+1" />
  <hr>
  <Student nickname="lisi" :IDCard="61212219920229"></Student>
 
</div>



</template>

<script>
import Student from "./components/Student.vue"
export default {
  name: 'App',
  components: {
    Student
  }
}
</script>

<style>

</style>
