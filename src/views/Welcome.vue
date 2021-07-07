<template>
  <div class="welcome container">
    <p>Welcome</p>
    <div v-if="isLogin">
      <h2>Login to the chatroom</h2>
      <LoginForm @login="enterChat" />
      <p>
        No account yet? <span @click="isLogin = false">Signup</span> instead
      </p>
    </div>
    <div v-else>
      <h2>Sign up to the chatroom</h2>
      <SignupForm @signup="enterChat" />
      <p>
        Already registered? <span @click="isLogin = true">Login</span> instead
      </p>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";
import { useRouter } from "vue-router";

import SignupForm from "../components/SignupForm.vue";
import LoginForm from "../components/LoginForm.vue";

export default {
  components: {
    SignupForm,
    LoginForm,
  },
  setup() {
    const isLogin = ref(true);
    const router = useRouter();

    const enterChat = () => {
      router.push("/chatroom");
    };

    return { isLogin, enterChat };
  },
};
</script>

<style>
.welcome {
  text-align: center;
  padding: 20px 0;
}
/* form styles */
.welcome form {
  width: 300px;
  margin: 20px auto;
}
.welcome label {
  display: block;
  margin: 20px 0 10px;
}
.welcome input {
  width: 100%;
  padding: 10px;
  border-radius: 20px;
  border: 1px solid #eee;
  outline: none;
  color: #999;
  margin: 10px auto;
}
.welcome span {
  font-weight: bold;
  text-decoration: underline;
  cursor: pointer;
}
.welcome button {
  margin: 20px auto;
}
</style>
