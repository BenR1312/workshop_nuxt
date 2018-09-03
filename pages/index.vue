<template>
  <section class="container">
    <div>
      <hello message="Hello, I am a component"/>
      <section>
        <p v-html="rawHTML" />
      </section>
      <section>
        <input type="text" v-model="firstName" placeholder="Enter firstname">
        <p>First Name: {{firstName}}</p>
      </section>
      <section>
        <button @click="counter -= 1">Remove 1</button>
        <p>The button above has been clicked {{ counter }} times.</p>
        <p v-if="counter >= 10">{{ counter }} in stock.</p>
        <p v-else-if="counter > 0">Hurry up, there are just a few items left!</p>
        <p v-else>Oops! Sorry, we're all out!</p>
      </section>
      <section>
        <button @click="isVisible = !isVisible">toggle</button>
        <h1 v-show="isVisible">Hello!</h1>
      </section>
      <section>
        <h4>TODOS</h4>
        <ul class="todos">
          <li v-for="(todo, index) in todos" :key="index">
            {{todo.title}}
          </li>
        </ul>
      </section>
      <section>
        <p>{{ reversedFirstName }}</p>
      </section>
      <section>
        {{ counter | toSGD }}
      </section>
    </div>
  </section>
</template>

<script>
  import Hello from '~/components/Hello.vue'
  export default {
    components: {
      Hello
    },
    data () {
      return {
        firstName: '',
        counter: 30,
        isVisible: true,
        todos: [
          {title: 'Meeting with Smelly'},
          {title: '1-on-1 with Bince'}
        ],
        rawHTML: '<h1>Luke!</h1> <span>I am your father.</span> '
      }
    },
    computed: {
      reversedFirstName() {
        return this.firstName.split('').reverse().join('')
      }
    },
    watch: {
      counter(newVal, oldVal) {
        if(newVal === 5) {
          this.updateInfo()
        }
      }
    },
    methods: {
      updateInfo(){
        alert('info updated!')
      }
    },
    filters: {
      toSGD: function (value) {
        return `S$${value}`;
      }
    }
  }
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}
.links {
  padding-top: 15px;
}
</style>
