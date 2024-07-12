<script setup>
import { reactive } from 'vue';


const estado = reactive({
  valor: 0,
  operacoes: ["soma", "subtracao", "multiplicacao", "divisao"]
});

function escolhaDaOperacao(evento){
  estado.valor = evento.target.value
  
}

function soma(){
  estado.valor + estado.valor
}
function subtracao(){
  valor - valor
}
function multiplicacao(){
  valor * valor
}
function divisao(){
  valor / valor
}

</script>

<template>
  <header>
    <div class="logo">
      <img alt="Vue logo" src="./assets/logo.svg" width="50" height="50" />
      <h1>Exercicio vue modulo 27</h1>
    </div>
  </header>

  <body>
    <div class="container">
      <section class="section__resultado">
            <h3>Resultado da Operação</h3>
            <span>{{ estado.valor }}</span>
      </section>

      <section class="section__operacao">
                <h3>Escolha a Operção</h3>
                <select>
                    <option v-for="operacao in estado.operacoes">{{ operacao }}</option>
                </select>
        </section>
    
          <section class="section__valor">
            <label for="">Digite o Valor</label>
            <div>
              <input @keyup="escolhaDaOperacao" type="number">
            </div>
          </section>

    </div>
    
  </body>
</template>

<style scoped>


.logo {
  padding: 10px;
  text-align: center;
  background-color: aqua
}

.logo h1{
  padding: 10px;
  border-bottom: 4px solid #000;
  background-color: aqua;
  text-shadow: 1px 2px 1px #fff;
}

.container {
  margin-top: 24px;
  text-align: center;
}


.section__resultado{
  color: blue;
  padding: 16px;
}

.section__valor{
  color: rgb(135, 23, 240);
  padding: 16px;
  display: flex;
  flex-direction: column;
}

.section__valor input{
  padding: 4px;
  margin-top: 16px;
  text-align: center;
  width: 200px;
  border-radius: 4px;
  background-color: #ccc;
  color: rgb(135, 23, 240);
}


.section__operacao{
  color: rgb(143, 24, 24);
  padding: 16px;
}

.section__operacao select{
  padding: 4px;
  text-align: center;
  width: 200px;
  margin-top: 16px;
  background-color: #ccc;
  color: rgb(143, 24, 24);
  border-radius: 4px;
}


@media (max-width: 768px) {
 

}
</style>
