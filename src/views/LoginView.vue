<template>
  <div class="page">
    <div class="card login-container">
      <h2 class="login-title">用户登录</h2>

      <input
        type="text"
        v-model="username"
        placeholder="请输入邮箱"
        class="login-input"
      />
      <div class="error-message" v-if="error && !username">用户名不能为空</div>

      <input
        type="password"
        v-model="password"
        placeholder="请输入密码"
        class="login-input"
      />
      <div class="error-message" v-if="error && !password">密码不能为空</div>

      <button @click="login" class="login-btn">登录</button>

      <div class="login-links">
        <span @click="goToRegister" class="login-link">注册</span>
        <span @click="goToForgotPassword" class="login-link">忘记密码?</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LoginView',
  data() {
    return {
      username: '',
      password: '',
      error: false,
    };
  },
  methods: {
    login() {
      this.error = false;
      if (!this.username || !this.password) {
        this.error = true;
        return;
      }
      alert(`欢迎，${this.username}！`);
      this.$router.push('/Browse');
    },
    goToRegister() {
      this.$router.push('/register');
    },
    goToForgotPassword() {
      this.$router.push('/forget-password');
    },
  },
};
</script>

<style scoped>
.page {
  background: #f5f5f5;

  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.login-container {
  width: 300px;
  padding: 40px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
  background: white;
  border-radius: 8px;
}

.login-title {
  text-align: center;
  margin-bottom: 20px;
  color: #333;
}

.login-input {
  width: 100%;
  padding: 12px;
  margin: 10px 0;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 14px;
  background: #fff;
}

.login-btn {
  width: 100%;
  padding: 12px;
  background-color: #409eff;
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  margin-top: 15px;
  transition: background 0.3s;
}

.login-btn:hover {
  background-color: #66b1ff;
}

.error-message {
  color: red;
  font-size: 12px;
  margin-top: -5px;
  margin-bottom: 10px;
}

.login-links {
  margin-top: 20px;
  text-align: center;
}

.login-link {
  color: #409eff;
  cursor: pointer;
  margin: 0 10px;
  font-size: 14px;
}

.login-link:hover {
  text-decoration: underline;
}
</style>
