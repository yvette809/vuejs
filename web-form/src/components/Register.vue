<template>
  <form @submit.prevent="handleSubmit">
    <label>Email:</label>
    <input type="email" required v-model="email" />
    <label>Password:</label>
    <input type="password" required v-model="Password" />
    <div v-if="passwordError">{{passwordError}}</div>
    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web developer</option>
      <option value="designer">web designer</option>
    </select>
    <label>skills:</label>
    <input type="text" v-model="tempskill" @keyup="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <span @click="deleteSkill(skill)"> {{ skill }}</span>
    </div>
    <div class="terms">
      <input type="checkbox" required v-model="terms" />
      <label>Accept terms and conditions</label>
    </div>
  </form>
  <div class="submit">
    <button>Create An Account</button>
  </div>
  <p>Email:{{ email }}</p>
  <p>password:{{ password }}</p>
  <p>Role:{{ role }}</p>
  <p>Terms accepted: {{ terms }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      terms: false,
      tempskill: "",
      skills: [],
      passwordError: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempskill) {
        if (this.skills.includes(this.tempskill)) {
          this.skills.push(this.tempskill);
        }
        this.tempskill = "";
      }
    },
    deleteSkill(skill) {
      this.skils = this.skills.filter((item) => {
        return skill != item;
      });
    },
    handleSubmit() {
      // validate password
      this.passwordError =
        this.password.length > 5 ? "" : "passwor must be atleast 6 chars long";
    },
  },
};
</script>

<style>
form {
  max-width: 420px;
  margin: 30px auto;
  background: #fff;
  text-align: left;
  padding: 40px;
  border-radius: 10px;
}
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.6rem;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: border-box;
  border: none;
  border-bottom: 1px solid #ddd;
}

input[type="checkbox"] {
  display: inline-block;
  width: 36px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
</style>
