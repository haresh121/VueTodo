<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
      <router-link to="/new">New</router-link>
    </div>
    <router-view/>
  </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css?family=Open+Sans');

body{
  margin:0;
  padding: 0;
  background-color: lightgoldenrodyellow;
  display: flex;
  align-content: center;
  justify-content: center;
  font-family: 'Open Sans', sans-serif;
}
#app{
  margin-top: 60px;
}
</style>
