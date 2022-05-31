<template>
  <h1>Sign Up</h1>
  <form @submit.prevent="handleSubmit">
    <label>EMAIL: </label>
    <input type="email" required v-model="email" />

    <label>PASSWORD: </label>
    <input type="password" required v-model="password" />
    <div v-if="passwordError">
      <p class="passwordWarning">{{ passwordError }}</p>
    </div>

    <label>ROLE: </label>
    <select v-model="role">
      <option value="full-stack-web">FullStack Web Developer</option>
      <option value="front-end-web">Front-end Web Developer</option>
      <option value="back-end-web">Back-end Web Developer</option>
    </select>

    <label class="skillHead">SKILLS: </label>
    <p class="addSkillHint">
      (Press <b>Alt +</b> to add new skill, to delete click on skill)
    </p>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>

    <div class="terms">
      <input type="checkbox" v-model="terms" required /><label
        >Accept T&C</label
      >
    </div>

    <div class="submit">
      <button>Create Account</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      terms: false,
      tempSkill: "",
      skills: [],
      passwordError: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "+" && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }
        this.tempSkills = "";
      }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item;
      });
    },
    handleSubmit() {
      // validate password
      this.passwordError =
        this.password.length > 5 ? "" : "password should be atleast 6 chars";

        if (!this.passwordError){
            console.log('email: ',this.email);
            console.log('password: ',this.password);
            console.log('role: ',this.role);
            console.log('skills: ',this.skills);
            console.log('terms accepted: ',this.terms);

        }
    },
  },    
};
</script>

<style>
form {
  padding: 40px 0;
  max-width: 400px;
  background: #fff;
  border-radius: 10px;
  text-align: left;
  padding: 40px;
  margin: 30px auto;
}
label {
  color: #0f4c7599;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 16px;
}
input {
  display: block;
  padding: 10px 5px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #444;
  color: #555;
  font-size: 20px;
}
input[type="email"] {
  text-transform: lowercase;
}
select {
  display: block;
  background: #fff;
  border: none;
  width: 100%;
  border-bottom: 1px solid #444;
  font-size: 20px;
  color: #555;
}
input[type="checkbox"] {
  display: inline-block;
  position: relative;
  width: 20px;
  margin: 0px 10px 0px 0px;
}
.pill {
  display: inline-block;
  background: #eee;
  padding: 6px 12px;
  margin: 20px 10px 0 0;
  font-weight: bold;
  letter-spacing: 1px;
  cursor: pointer;
  color: #0f4c75;
  border-radius: 20px;
}
.skillHead {
  position: relative;
  padding-right: 5px;
}
.addSkillHint {
  display: inline-block;
  position: relative;
  opacity: 90%;
  font-size: 13px;
}
.submit button{
  border-radius: 20px;
  background-color: #3282b899;
  box-shadow: 1px 1px 15px #ffffff50;
  border: none;
  font-size: 22px;
  padding: 5px 25px 5px 25px;
  margin: 10px;
  cursor: pointer;
}
.submit button:hover {
  margin-top: 10px;
  box-shadow: 1px 1px 15px #00000099;
  color: #000;
  transform: translateY(-10px);
  transition: all 0.3s;
}
.submit {
  display: flex;
  justify-content: center;
}
.passwordWarning {
  color: red;
  padding-top:5px;
}
</style>