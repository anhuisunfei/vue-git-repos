<template>
  <div id="app">
    <header>
        <h1>欢迎来到VueJs</h1>
      <vue-particles  color="#dedede"></vue-particles>

    </header>
    <main>
       <router-view/>
    </main>

  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app header {
  height: 45vh;
  background-color: #00bcd4;
  color: blue;
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  background: linear-gradient(#0097a7, #00bcd4);
  background-size: 250% 250%;
  animation: kKvztC 10s ease infinite;
  font-weight: 400;
  transition: height 250ms ease-in-out;
  user-select: none;
}
#app header h1 {
  display: flex;
  flex-wrap: wrap;
  font-size: 1.5rem;
  text-transform: uppercase;
  font-weight: 700;
  align-items: center;
  transition: font-size 250ms ease-in-out, padding 150ms ease-in;
  background-color: #002635;
  color: white;
  padding: 0.5rem 1rem;
  margin: 0;
  width: auto;
  user-select: text;
}
@media only screen and (min-width: 375px) {
  #app header h1 {
    font-size: 2rem;
  }
}
@media only screen and (min-width: 768px) {
  #app header h1 {
    font-size: 3.5rem;
    padding: 1rem 2rem;
  }
}
#app main {
  position: absolute;
  top: 40vh;
  right: 0;
  left: 0;
  margin: 0 auto;
  max-width: 840px;
  z-index: 2;
}
#particles-js{
  position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    width:100%;
    height:100%;
}
</style>
