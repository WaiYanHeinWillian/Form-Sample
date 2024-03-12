<template>
  <form v-on:submit.prevent="submit">
    <label>Email</label>
    <input type="email" required v-model="email">
    <label>Password</label>
    <input type="password" required v-model="password">
    <p class="errmsg" v-if="errMsg">{{errMsg}}</p>
    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="QA">Quality Assurance</option>
    </select>
    
            <!-- %%% Single checkbox %%% -->
    <div>
      <input type="checkbox" v-model="check">
      <label>Accept terms & conditions</label>
    </div>

                <!-- %%% Multi checkbox %%% -->
    <label>Choose you skills:</label>
    <div>
      <input type="checkbox" value="HTML/CSS" v-model="skill">
      <label>HTML</label>
    </div>
    <div>
      <input type="checkbox" value="Java" v-model="skill">
      <label>Javascript</label>
    </div>
    <div>
      <input type="checkbox" value="Vue" v-model="skill">
      <label>VueJS</label>
    </div>
    <div>
      <input type="checkbox" value="LLV" v-model="skill">
      <label>Laraval</label>
    </div>

    <div>
      <label>Choose Your Skills:</label>
      <input type="text" v-on:keyup.alt="inputSkill" v-model="tpedSkill">
    </div>
    <div v-for="bySkill in skillArray" v-bind:key="bySkill">
      <p>{{bySkill}}<span class="cross" @click="deleteSkill(bySkill)">&#10007;</span></p>
    </div>

    <div class="align">
      <button class="submitButton">Create Account</button>
    </div>
  </form>

  <!-- I'm = {{email}}&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;,&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  You are = {{password}}<br>
  what's role {{role}}<br>
  The check box is {{check}}<br>
  You skills are {{skill}}<br> -->
  
  <br><br><br>
</template> 

<script>
export default {
  data(){
    return{
      email:"",
      password:"",
      role:"",
      check:false,
      skill:[],
      tpedSkill:"",
      skillArray:[],
      errMsg:"",
    }
  },
  
  methods:{
    inputSkill(e){
      if(e.key===','){
        this.skillArray.push(this.tpedSkill);
        this.tpedSkill="";
      }
    },
    deleteSkill(dskill){
      this.skillArray=this.skillArray.filter(loopSkill=>{
        return loopSkill!=dskill;
      })
    },
    submit(){
      console.log("submiting!!");
      if(this.password.length<8){
        this.errMsg="Password should be valid!";
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
    input,select {
        display: block;
        padding: 10px 6px;
        width: 100%;
        box-sizing: border-box;
        border: none;
        border-bottom: 1px solid #ddd;
        color: #555;
    }
    input[type="checkbox"]{
      display: inline-block;
      width: 16px;
      margin: 0 10px 0 0;
      position: relative;
      top: 2px;
    }
    .cross{
      color: red;
      margin: 0 0 0 30px;
      cursor: pointer;
    }
    .submitButton{
      background-color: royalblue;
      padding: 7px;
      color: azure;
      border-radius: 10px;
      margin: 10px auto;
      
    }
    .align{
      text-align: center;
    }
    .errmsg{
      color: crimson;
    }
</style>