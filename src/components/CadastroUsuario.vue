<!-- CadastroUsuario.vue -->

<template>
  <div class="container">
    <h2>Cadastro de Usuário</h2>
    <form @submit.prevent="registerUser" class="form">
      <div class="form-group">
        <label for="name">Nome:</label>
        <input type="text" id="name" v-model="formData.name" required />
      </div>
      <div class="form-group">
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="formData.email" required />
      </div>
      <div class="form-group">
        <label for="password">Senha:</label>
        <input
          type="password"
          id="password"
          v-model="formData.password"
          required
        />
      </div>
      <button type="submit">Cadastrar</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      formData: {
        name: "",
        email: "",
        password: "",
      },
    };
  },
  methods: {
    registerUser() {
      axios
        .post("http://127.0.0.1:8000/api/register", this.formData)
        .then((response) => {
          window.alert(`Cadastro de ${this.formData.name} feito com sucesso!`);
        })
        .catch((error) => {
          window.alert("Erro ao cadastrar usuario!");
          console.error("Erro ao cadastrar usuario:", error.response.data);
        });
    },
  },
};
</script>

