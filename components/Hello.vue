<template>
  <div>
    <p class="hello">{{message}}</p>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        message: 'Hello, I am a component'
      }
    }
  }
</script>

<style>
.hello {
  color: red;
}
</style>
