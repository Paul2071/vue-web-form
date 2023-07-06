<template>

    <form @submit.prevent="handleSubmit">
        <label> Paint Name</label>
        <input type="paint" required v-model="paint" >

        <label > Type of Paint</label>
        <input type="type" required v-model="type" placeholder="Contrast / base / layer etc..." >
        <div v-if="typeError" class="error">
          {{ typeError }}
        </div>

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
          <div v-for="skill in skills" :key="skill" class="pill" >
            <span @click="onClick(skill)"> {{  skill  }}  </span>        
          </div>

          <div class="button">
            <button>create</button>
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
      typeOptions:["contrast", "base", "layer"],
      dropdown: "citadel",
      terms: false,
      tempSkill: "",
      skills: [],
      typeError: ""
      
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
    },

    onClick (skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item
      })
    },
    handleSubmit() {
     
      if ( this.type === this.typeOptions[0]  ) {
        this.typeError = "type accepted"
      } else if ( this.type === this.typeOptions[1]  ) {
        this.typeError = "type accepted"
      } else if ( this.type === this.typeOptions[2]  ) {
        this.typeError = "type accepted"
      }  
      
      else {
        this.typeError = "Not valid type"
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
  .pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
    cursor: pointer;
  }
  button {
    background: #0b6dff;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: aliceblue;
    border-radius: 20px;
  }
  .submit {
    text-align: center;
  }
  .error {
    color: #ff0062;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
  }


</style>