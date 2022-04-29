<template>
<br>
<br>
<div class="sidebar1">
  <label for="start">From date</label>
  <br>
  <input 
    type="date" 
    id="start" 
    name="trip-start" 
    value="2019-01-01" 
    min="2019-01-01" 
    max="2019-01-31"
    class="input">
  <br>
  <br>
    <label for="start">To date</label>
  <br>
  <input 
    type="date" 
    id="start" 
    name="trip-start" 
    value="2019-01-01" 
    min="2019-01-01" 
    max="2019-01-31"
    class="input">
  <br>
  <br>
  <label for="">Bill Number</label>
  <br>
  <input class="input" type="number">
  <br>
  <br>
  <br>
    <button class="button" @click ="$emit('get-data')">Search</button>
</div>
</template>

<script>

export default {
    name: "Sidebar",
}
</script>

<style>
  .input{
    width: 200px;
    height: 25px;
    text-align: center;
  }
  .button{
    background-color: #3267E3;
    width: 207px;
    height: 30px;
    border-radius: 5px;
    cursor: pointer;
    color: aliceblue;
    border: none;
  }
  .sidebar1{
    padding-left: 13px;
  }
</style>