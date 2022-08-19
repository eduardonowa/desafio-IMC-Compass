<template>
  <div class="calc-container">
    <h1>{{ titleMsg }}</h1>
    <InputRange
      inputId="weightInput"
      labelInput="Peso"
      maxRange="150"
      minRange="0"
      step="1"
      :valueSelected="weightSelected"
      :event="getValue"
      measure="kg"
    />
    <InputRange
      inputId="heightInput"
      labelInput="Altura"
      maxRange="2.20"
      minRange="1"
      step="0.01"
      :valueSelected="heightSelected"
      :event="getValue"
      measure="m"
    />
    <button class="calcButton" @click.prevent="calcImc">{{ buttonTxt }}</button>
    <span id="spanMsg">{{ spanMsg }}</span>
    <h3 id="result">IMC: {{ imc }} ({{ condition }}).</h3>
  </div>
</template>

<script>
import InputRange from "@/components/InputRange/InputRange.vue";
export default {
  name: "CalcBox",
  components: {
    InputRange,
  },
  data() {
    return {
      weightSelected: "",
      heightSelected: "",
      spanMsg: "Peso inválido.",
      imc: "",
      condition: "",
      titleMsg: "Calcule seu IMC",
      buttonTxt: "Calcular",
    };
  },
  methods: {
    calcImc() {
      const $ = document.getElementById.bind(document);
      if (this.weightSelected != 0) {
        const resultado =
          this.weightSelected / Math.pow(this.heightSelected, 2);
        this.imc = resultado.toFixed(2);
        $("result").style.visibility = "visible";
        $("spanMsg").style.visibility = "hidden";
      } else {
        $("result").style.visibility = "hidden";
        $("spanMsg").style.visibility = "visible";
      }
      if (this.imc <= 18.5) {
        this.condition = "Abaixo do Peso";
      } else if (this.imc <= 24.9) {
        this.condition = "Peso Normal";
      } else if (this.imc <= 29.9) {
        this.condition = "Sobrepeso";
      } else if (this.imc <= 34.9) {
        this.condition = "Obesidade Grau I";
      } else if (this.imc <= 39.9) {
        this.condition = "Obesidade Grau II";
      } else if (this.imc > 40) {
        this.condition = "Obesidade Mórbida";
      }
    },

    getValue() {
      this.weightSelected = document.getElementById("weightInput").value;
      this.heightSelected = document.getElementById("heightInput").value;
    },
  },
  beforeMount() {
    this.weightSelected = "60";
    this.heightSelected = "1.5";
  },
  computed: {},
};
</script>

<style lang="scss" scooped>
@import "./CalcBox.scss";
</style>
