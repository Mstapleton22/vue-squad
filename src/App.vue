<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/about">About</router-link>|
      <router-link to="/squad">Squad</router-link>
    </div>
    <router-view :uselessSuperheroes="uselessSuperheroes"/>
  </div>
</template>

<script>
export default {
  data() {
    return {
      uselessSuperheroes: null
    };
  },
  methods: {
    getUselessSuperheroes() {
      fetch("https://g107-db.herokuapp.com/students")
        .then(resp => resp.json())
        .then(resp => (this.uselessSuperheroes = resp.students));
    }
  },
  mounted() {
    this.getUselessSuperheroes();
  }
};
</script>


<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  display: flex;
  justify-content: flex-end;
  background-color: navy;
}

#nav a:hover {
  color: white;
}

#nav a {
  font-weight: bold;
  color: lightblue;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
