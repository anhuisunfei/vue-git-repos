<template>
  <div>
    <section class="section" v-for="item in items" :key="item.id" >
      <span class="tool-bar" :style="{'background-color':item.color}">{{moment(item.created_at).format('YYYY-MM-DD')}}</span>
      <div class="section-content">
          <hr class="split-bar">
          <h1 class="content-title">{{item.name}}</h1>
          <hr class="split-bar">
      </div>
      <a class="read-more" target="_blank" v-bind:href="item.clone_url">READ MORE</a>
    </section>
  </div>
</template>

<script>
import axios from 'axios'
import {getColorFromString} from '../utils/color'

export default {
  created () {
    axios.get('https://api.github.com/users/anhuisunfei/repos?sort=created&order=desc')
      .then(res => {
        res.data.forEach(el => {
          el.color = getColorFromString(el.name)
          console.log(el.color)
        })
        this.items = res.data
      })
      .catch(err => {
        console.log(err)
      })
  },
  data () {
    return {
      items: []
    }
  }
}
</script>

<style>
.section {
  position: relative;
  width: 100%;
  background-color: white;
  box-shadow: 0 0 4px 1px rgba(0, 0, 0, 0.2);
  background-color: white;
  outline: 1px solid rgba(0, 0, 0, 0.125);
  box-shadow: 0 0 4px 1px rgba(0, 0, 0, 0.2);
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-bottom: 1.5rem;
  :last-child {
    border-bottom-width: 0;
  }
}
.tool-bar {
  display: -webkit-box;
  display: -webkit-flex;
  display: -ms-flexbox;
  display: flex;
  width: 100%;
  -webkit-box-pack: center;
  -webkit-justify-content: center;
  -ms-flex-pack: center;
  justify-content: center;
  z-index: 1;
  background: hsl(166, 90%, 20%);
  color: white;
  position: relative;
  -webkit-transition: background-color 125ms ease-in-out;
  transition: background-color 125ms ease-in-out;
  padding-top: 1.125rem;
  padding-bottom: 1.125rem;
}
@media only screen and (min-width: 768px) {
  .section {
    margin-bottom: 3rem;
    padding-bottom: 3rem;
  }
}
.section-content {
  max-width: 100%;
  padding: 1.125rem 1.5rem;
}
@media only screen and (min-width: 768px) {
  padding: 1.5rem 3rem;
  padding-top: 1.5rem;
}
.split-bar {
  border: 0;
  width: 75%;
  margin: 0.75rem auto;
  border-bottom: 1px solid #eee;
}

.content-title {
  font-size: 1.25rem;
  line-height: 1.5rem;
  text-align: center;
  margin-bottom: 0;
}
@media only screen and (min-width: 768px) {
  .content-title {
    font-size: 1.5rem;
    line-height: 2.25rem;
  }
}

.read-more {
  display: inline-block;
  background-color: white;
  padding: 0.5rem 1.5rem;
  font-size: 1.125rem;
  font-weight: bold;
  text-decoration: none;
  text-align: center;
  text-transform: uppercase;
  border-width: 2px;
  border-style: solid;
  -webkit-transition: all 125ms ease-in-out;
  transition: all 125ms ease-in-out;
  font-family: sans-serif;
  background-color: hsl(166, 90%, 20%);
  color: white;
  border-color: hsl(166, 90%, 20%);
}
</style>



