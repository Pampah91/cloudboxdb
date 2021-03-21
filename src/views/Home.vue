<template>
  <div class="home">
    <UserForm/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import UserForm from '@/components/UserForm.vue'

export default {
  name: 'Home',
  components: {
    HelloWorld, UserForm
  }
}
</script>
