<template>
  <div>
    <header>
      <h1>Vue Dynamic Styling</h1>
    </header>
    <section id="styling">
      <div 
       class="demo"
      :class="boxAClasses" 
      @click="boxSelected('A')"
      ></div>
      <div 
      class="demo" 
      :class="['demo', {active: boxBSelected}]" 
      @click="boxSelected('B')"></div>
      <div 
      class="demo" 
      :class="{active: boxCSelected}" 
      @click="boxSelected('C')"></div>
    </section>
  </div>
</template>

<script>
  export default {
    name: 'VueStyle',
    data(){
      return {
        boxASelected: false,
        boxBSelected: false,
        boxCSelected: false
      }
    },
    computed: {  // do dynamicznych styli 
      boxAClasses() {
        return {active: this.boxASelected}
      }
    },
    methods: {
      boxSelected(box) {
        if (box === 'A') {
            this.boxASelected = !this.boxASelected;
        } else if (box === 'B') {
            this.boxBSelected = !this.boxBSelected;
        } else if (box === 'C') {
            this.boxCSelected = !this.boxCSelected;
        }
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
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  background-color: #4fc08d;
  color: white;
  text-align: center;
}

#styling {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
}

.demo {
  width: calc(100% - 32px);
  height: 100px;
  margin: 16px;
  border: 2px dashed #ccc;
}

.active {
  border-color: red;
  background-color: salmon;
}
</style>