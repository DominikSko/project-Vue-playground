<template>
  <div>
    <header>
      <h1>Vue Events</h1>
    </header>
    <section id="events">
      <h2>Events in Action</h2>
      <button @click.left="add(10)">Add 10</button>
      <button @click="reduce(5)">Reduce 5</button>
      <p v-once>Starting Counter: {{ counter }}</p>
      <p>Result: {{ counter }}</p>
      <input 
        type="text" 
        v-model="name">
        <!-- v-on:input="setName($event, 'Kowalski')" 
             v-on:keyup.enter="confirmedImput"> v-model to robi! 
             v-on:click -> @click, v-bind:click -> :click     -->
      <input 
        type="text" 
        v-model="lastName">
      <button v-on:click="resetInput">Reset Input</button>
      <p>Your Name: {{ fullName }}</p>
      <form 
        v-on:submit.prevent="submitForm">
        <button>Sign Up</button>
      </form>
    </section>
  </div>
</template>

<script>

export default {
  name: 'myName',
  props: {
    msg: String
  }, 
  data() {
    return {
      counter: 0,
      name: '',
      confirmedName: '',
      lastName: ''
    };
  },
  watch: {  // watchers, for optimalization, http requests, timers, for watching
    counter(value) {
      if (value > 50){
        const that = this;
        setTimeout(function () {
          that.counter = 0;
        }, 2000);
      }
    }
    // name(value) {
    //   if (value === ''){
    //     this.fullname = ''
    //   } else {
    //     this.fullname = value + '' + this.lastName;
    //   }
    // },
    // lastName(value){
    //   if (value === ''){
    //     this.fullname = ''
    //   } else {
    //     this.fullname = this.name + '' + value;
    //   }
    // }
  },
  computed: { // aby vue nie wywylowal metody z html za kazdym razem, do wyswietlania danych a nie odswiezania co chwile, optymalizacja
    fullName() {
      console.log('Running this method again...')
      if (this.name === '' || this.lastName === '') {
        return '';
      } 
      return this.name + '' + this.lastName;
    }
  },
  methods: {
    confirmedImput() {
      this.confirmedName = this.name;
    },
    outputFullname(){
      console.log('Running this method again...')
      if (this.name === '') {
        return '';
      } 
      return this.name + '' + 'Kowalski?';
    },
    add(num) {
      this.counter = this.counter + num;
    },
    reduce(num) {
      this.counter = this.counter - num;
    },
    setName(event, lastName) {
      this.name = event.target.value + '' + lastName;
    },
    submitForm() {
      alert('Submitted');
    },
    resetInput() {
      this.name = '';
      this.lastName = '';
    }
  }
}

</script>

<style scoped>

* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #4fc08d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#events {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#events h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #4fc08d;
  margin: 0 0 1rem 0;
}

#events p {
  font-size: 1.25rem;
  font-weight: bold;
  border: 1px solid #4fc08d;
  background-color: #4fc08d;
  color: white;
  padding: 0.5rem;
  border-radius: 25px;
}

#events input {
  font: inherit;
  border: 1px solid #ccc;
}

#events input:focus {
  outline: none;
  border-color: #1b995e;
  background-color: #d7fdeb;
}

#events button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
  border-radius: 20px;
  margin: 0 1rem;
}

#events button:hover,
#events button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

</style>