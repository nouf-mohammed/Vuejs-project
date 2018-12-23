<template>
  <div class="hello">

    <form @submit.prevent="login">
    <div class="container">
      <label for="uname"><b>اسم المستخدم</b></label><br>
      <input type="text" placeholder="Enter Username"
             name="username" v-model="input.username" required>
      <br><br>
      <label for="psw"><b>كلمة المرور</b></label><br>
      <input type="password" placeholder="Enter Password"
             name="pssword" v-model="input.password" required>
      <br><br>
      <button type="submit" >تسجيل الدخول</button>
      <label><br><br>
        <input type="checkbox" checked="checked" name="remember"> Remember me
      </label>
    </div>

    </form>
  </div>
</template>

<script>
export default{
  el: 'HelloWorld',
  data() {
    return {
      input: {
        username: '',
        password: '',
      },
    };
  },
  methods: {
    login() {
      if (this.input.username === this.$parent.mockAccount.username
        && this.input.password === this.$parent.mockAccount.password) {
        this.$emit('authenticated', true);
        this.$router.push({ name: 'content' });
      } else {
        this.input.password = 'h';
      }
    },
  },


};

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

  form {border: 2px solid #f1f1f1;}
  input[type=text], input[type=password] {
    width: 30%;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid #ccc;
    box-sizing: border-box;
  }

  button {
    background-color: #46af82;
    color: white;
    padding: 14px 20px;
    margin: 8px 0;
    border: none;
    cursor: pointer;
    width: 30%;
  }

  button:hover {
    opacity: 0.8;
  }

  .cancelbtn {
    width: auto;
    padding: 10px 18px;
    background-color: #f44336;
  }


  .container {
    padding: 16px;
  }

  span.psw {
    float: right;
    padding-top: 16px;
  }

  /* Change styles for span and cancel button on extra small screens */
  @media screen and (max-width: 300px) {
    span.psw {
      display: block;
      float: none;
    }
    .cancelbtn {
      width: 100%;
    }
  }
</style>
