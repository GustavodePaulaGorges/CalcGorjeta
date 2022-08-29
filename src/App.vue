<script>
export default {
  data() {
    return {
      qualities: [
        { quality: 5, service: "5% - Péssimo" },
        { quality: 10, service: "10% -Ruim" },
        { quality: 15, service: "15% - OK" },
        { quality: 20, service: "20% - Bom" },
        { quality: 25, service: "25% - Mais que bom" },
        { quality: 30, service: "30% - Excelente" },
      ],
      value: 0,
      people: 1,
      selected_quality: "",
    };
  },
  computed: {
    final_value() {
      return (
        (this.value * (1 + this.selected_quality / 100)) / this.people).toFixed(2);
    },
  },
};
</script>

<template>
  <div>
    <div >
      <form action="" class="FormMenu">
        <label for="valorConta"> <p class="MenuText">Valor do serviço:</p></label>
        <input name="valorConta" class="MenuInput"  v-model="value" type="number" />

        <label for="porcentagemServico"> <p class="MenuText">Avaliação do serviço</p> </label>
        <select class="MenuInput" v-model="selected_quality">

          <option value="" disabled selected>escolha aqui!</option>
          <option v-for="quality of qualities" :key="quality.quality" for="select-service" :value="quality.quality">
            {{ quality.service }}
          </option>

          </select>
          
          <label for="NumPeople"> <p class="MenuText">Nº de pessoas pagando a conta:</p> </label
        ><input name="NumPeople" class="MenuInput" type="number" v-model="people" />
      </form>

      <div class="result">
        <p>Valor da conta por pessoa:</p>
        <span>R$ {{ final_value }}</span>
      </div>
    </div>
  </div>
</template>

<style>
.FormMenu{
  outline: black solid 1px;
  width: min-content;
  text-align: center;
  padding: 10px;
  background-color: #FFF;
  box-shadow: 0.3vh 0.3vh 0.5vh black;
}
.MenuText{
  font-size: 2vh;
  color: #FFF;
  background-color: black;
  padding: 0.1vh;
  font-weight: bold;
  font-family: 'Ubuntu', sans-serif;
}
.MenuInput{
  width: 20vh;
  margin-bottom: 1vh;
  text-align: center;
  outline: 1px solid lightgray;
}
.result{
  background-color: #FFF;
  font-family: 'Ubuntu', sans-serif;
  color: black;
  text-align: center;
  outline: black 1px solid;
  box-shadow: 0.3vh 0.3vh 0.5vh black;
}

</style>
