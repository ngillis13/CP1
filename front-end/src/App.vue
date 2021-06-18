<template>
  <div id="app">
    <div id="nav">
       <p> Weclome to Rate that movie! </p>
    </div>
    <router-view/>
    <div id = "footer">
    <p> Hours wroked: 12 </p>
      <a href="https://github.com/ngillis13/CP1">github repository</a>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  font-size: 50px;
  color: white;
  background: grey;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

#footer {
  background: black;
  position: absolute;
  font-size: 20px;
  bottom: 0px;
  width: 100%;
  color: white;
}
</style>
