<template>
  <link
    rel="stylesheet"
    href="https://pro.fontawesome.com/releases/v5.10.0/css/all.css"
    integrity="sha384-AYmEC3Yw5cVb3ZcuHtOA93w35dYTsvhLPVnYs9eStHfGJvOvKxVfELGroGkvsg+p"
    crossorigin="anonymous"
  />

  <div id="app">
    <div class="container">
      <div class="wrapper">
        <div class="header">
          <h4>Clientes</h4>
        </div>
        <div class="search">
          <i onclick="pesquisar()" class="fas fa-search"></i>
          <input
            id="inputTaskTxtId"
            class="inputTaskTxt"
            type="text"
            placeholder="Pesquise nome ou companhia"
          />
        </div>
        <ul id="list-ul">
          <li v-for="usuario of usuarios" :key="usuario.id" class="list-item">
            <div class="img-wrapper">
              <img src="./assets/img/user.png" alt="" />
            </div>
            <div class="user-details">
              <h4>{{ usuario.name }}</h4>
              <p>{{ usuario.company.bs }}</p>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Usuario from "./services/usuarios";

export default {
  data() {
    return {
      usuarios: [],
    };
  },
  mounted() {
    Usuario.list().then((res) => {
      console.log(res.data);
      this.usuarios = res.data;
    });
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;700&display=swap");

body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}
h4,
p {
  margin: 0;
}
#app {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100vw;
  height: 100vh;
  font-family: "Poppins", sans-serif;
}
.container {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: linear-gradient(
    to right,
    #a970ff 0%,
    #a970ff 50%,
    #0f0f13 50%,
    #0f0f13 100%
  );
}
.wrapper {
  width: 75%;
  height: 90%;
  background: #efbdeb;
  border-radius: 1rem 1rem 0rem 0rem;
}
.header {
  width: 100%;
  height: 7.5%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 24px;
  color: black;
  background: #96e8bc;
  text-transform: uppercase;
  border-radius: 1rem 1rem 0rem 0rem;
}
.search {
  height: 5%;
  width: 25%;
  background: white;
  position: absolute;
  transform: translate(185%, 0px);
  margin-top: 25px;
  padding-left: 15px;
  border-radius: 25px;
  display: flex;
  align-items: center;
}
.search i {
  cursor: pointer;
  color: black;
  font-size: 20px;
}
.inputTaskTxt {
  border: none;
  background: none;
  outline: none;
  width: 80%;
  margin: 0;
  overflow: hidden;
  padding-left: 5px;
  /* height: 75%; */
}
#list-ul {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: flex-start;
  height: 92.5%;
}
.list-item {
  padding-left: 1rem;
  /* margin-top: 1rem; height acima faz isto ficar desnecessario e faz responsividade automatica*/
  display: flex;
  align-items: center;
  justify-content: start;
}
.list-item:nth-child(1) {
  margin-top: none;
}
.list-item h4 {
  color: #0a81d1;
}
.list-item p {
  color: #a0a08c;
  padding-left: 0.5rem;
  font-size: 14px;
}
.img-wrapper {
  width: 28px;
  height: 28px;
  border-radius: 50%;
  overflow: hidden;
}
.img-wrapper img {
  width: 100%;
  height: 100%;
  cursor: pointer;
}
.user-details {
  margin-left: 1rem;
}
</style>
