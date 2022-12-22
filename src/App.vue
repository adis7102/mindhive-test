<template>
  <router-view/>
</template>

<script>
import './styles/_fonts.scss';

export default {
  name: 'App'
}
</script>

<style>
body {
  margin: 0;
}

#app {
  font-family: SF-Pro;
}

input:focus, select:focus{
  outline: none;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type=number] {
  -moz-appearance:textfield;
}

</style>