<template>
  <div class="login-container">
    <form @submit.prevent="submitLogin">
      <h2>Faça o login</h2>
      <label>
        Usuário:
        <input type="text" v-model="username" />
      </label>
      <label>
        Senha:
        <input type="password" v-model="password" />
      </label>
      <button type="submit">Entrar</button>
    </form>
    <hr />
    <form @submit.prevent="submitSignup">
        <h2>Crie sua conta</h2>
        <label>
          Nome de usuário:
          <input id="inputUsername" type="text" v-model="newUsername" />
        </label>
        <label>
          Senha:
          <input type="password" v-model="newPassword" />
        </label>
        <button type="submit">Criar conta</button>
      </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
      newUsername: '',
      newPassword: '',
      users: []
    };
  },
  methods: {
    submitLogin() {
      const user = this.users.find(
        u => u.username === this.username && u.password === this.password
      );
      if (user) {
        window.alert('Autenticado com sucesso!');
        // Implemente aqui a lógica para redirecionar o usuário para a página protegida
      } else {
        window.alert('Usuário ou senha inválidos');
        // Implemente aqui a lógica para exibir uma mensagem de erro ao usuário
      }
    },
    submitSignup(){
      this.users.push({ username: this.newUsername, password: this.newPassword});
      window.alert('Conta criada com sucesso!');
      document.getElementById('inputUsername').value = '';
      this.newPassword = '';
      this.newUserName = ''
      console.log(this.users);
    }
  }
};
</script>

<style>
.login-container {
  width: 400px;
  margin: 0 auto;
  text-align: center;
}

form {
  margin-top: 50px;
}

input[type="text"],
input[type="password"] {
  padding: 10px;
  width: 100%;
  margin-top: 10px;
  font-size: 16px;
  box-sizing: border-box;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button[type="submit"] {
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  margin-top: 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button[type="submit"]:hover {
  background-color: #3e8e41;
}
</style>