<template>

    <form>
        <label> Paint Name</label>
        <input type="paint" required v-model="paint" >

        <label > Type of Paint</label>
        <input type="type" required v-model="type" placeholder="Contrast / base / layer etc..." >

        <label>Brand</label>
        <select v-model="dropdown">
          <option value="citadel"> Citadel </option>
          <option value="vallejo"> Vallejo </option>
        </select>

          <div class="terms">
            <input type="checkbox" v-model="terms" required>
            <label>Accept T&Cs </label>
            <p>Terms accepted: {{ terms }}</p>
          </div>

          <label>Skills</label>
          <input type="text" v-model="tempSkill" @keyup.alt="addSkill" >
          <div v-for="skill in skills" :key="skill" class="pill">
            {{  skill  }}
          
          </div>

    </form>

    <p> {{ paint }}</p>
    <p> {{ type }}</p>
    <p> {{ dropdown }}</p>
   

</template>

<script>

export default {
  data () {
    return {

      paint: " ",
      type: "",
      dropdown: "citadel",
      terms: false,
      tempSkill: "",
      skills: []
      
    }
  },
  methods: {
    addSkill(e){
      if(e.key === "," && this.tempSkill){
        if(!this.skills.includes(this.tempSkill)){

       

          this.skills.push(this.tempSkill)
        }

        this.tempSkill=""
      }
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
  input, select {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;   
    color: #555;    
    border-width: 1px;
    border-style: solid;
  }
  input[type="checkbox"]{
    display: inline-block;
    width: 16px;
    margin: 0 10px, 0 0;
    position: relative;
    top: 2px;
  }

</style>