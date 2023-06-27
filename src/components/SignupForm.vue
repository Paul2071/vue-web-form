<template>

    <form>
        <label> Paint Name</label>
        <input type="paint" required v-model="paint">

        <label> Type of Paint</label>
        <input type="type" required v-model="type">
    </form>

    <p> {{ paint }}</p>
    <p> {{ type }}</p>

</template>

<script>

export default {
  data () {
    return {

      paint: " ",
      type: ""
    }
  }
}

</script>

<style>
form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;
    border-radius: 10px;
    border: #555;
    border-width: 1px;
    border-style: solid;
  }
  label {
    color: #aaa;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
    
   
  }
  input {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;   
    color: #555;    
    border-width: 1px;
    border-style: solid;
  }
</style>