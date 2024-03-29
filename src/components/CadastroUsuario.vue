<template>
  <div class="container">
    <img src="../assets/img/login.jpg" alt="imagem de login" />
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
<style>
img {
  width: 250px;
  height: auto;
}
h2 {
  color: #007dfe;
}
.container {
  padding: 10px;
  border-radius: 15px;
  border: 1px solid #007dfe;
}
.form-group {
  display: flex;
  flex-direction: column;
}
label {
  color: #007dfe;
  display: flex;
  flex-direction: flex-start;
}

input {
  border: none;
  border-radius: 10px;
  background-color: #a6c9ff;
  padding: 5px;
  height: 25px;
  transition: border-color 0.3s ease; /* Adiciona transição para a mudança de cor da borda */
}
input:focus {
  border-color: #007dfe; /* Muda a cor da borda quando o input é focado */
}
button {
  border: none;
  background: #007dfe;
  color: #e9e9e9;
  width: 100%;
  margin-top: 10px !important;
  transition: background-color 0.3s ease, color 0.3s ease; /* Adiciona transições suaves para a mudança de cor do botão */
}
button:hover {
  border: none;
  background: #a6c9ff;
  color: #2f2f30;
}
</style>

