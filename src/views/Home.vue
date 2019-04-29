<template>
  <div class="home">
    <div class="form-container" v-show="showForm">
      <h1>Join the Web Developers Club!</h1>
      <p>Sign up to access our secret squirrel page. Just create an account and answer a brief survey.</p>

      <p
        class="error"
        v-show="showError"
      >Uh oh. Something didn't work. Take a look to see if you missed something.</p>

      <form v-on:submit.prevent="validateForm">
        <p>
          <label for="username">
            Username:
            <input type="text" id="username" v-model="username">
          </label>
        </p>

        <p>
          <label for="email">
            Email:
            <input type="text" id="email" v-model="email">
          </label>
        </p>

        <p>
          <label for="password">
            Password:
            <input type="text" id="password" v-model="password">
          </label>
        </p>

        <p>
          <label for="passwordVerify">
            Please verify password:
            <input type="text" id="passwordVerify" v-model="passwordVerify">
          </label>
        </p>

        <p>
          <input type="submit" value="Submit">
        </p>
      </form>
    </div>
    <div class="success-message" v-show="!showForm">
      <h1>Thank you for signing up and check your inbox for our VIM (Very Important Messages).</h1>
      <h2>
        Please take our new member survey. There's a chance you might get a secret decoder ring as a thank you.
        <p>
          <router-link to="/survey">Click here</router-link>
        </p>
      </h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "Home",
  data() {
    return {
      username: "",
      email: "",
      password: "",
      passwordVerify: "",
      showForm: true,
      showError: false
    };
  },
  methods: {
    validateForm: function() {
      if (
        this.username != "" &&
        this.email != "" &&
        this.password === this.passwordVerify
      ) {
        this.showForm = false;
      } else {
        this.showError = true;
      }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  border: 1px solid #aa0000;
  padding: 1rem;
  color: #aa0000;
}
h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
