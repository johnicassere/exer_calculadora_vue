<script setup>
import { reactive } from 'vue';

const estado = reactive({
    operacao: "",
    valor: 0,
    valorIput1: '',
    valorIput2: '',
    textoInicial:"Você Escolheu " 
     
});

function opEscolhida(oper) {
    estado.valorIput1 = '';
    estado.valorIput2 = '';
    if(estado.operacao == ''){
    alert("Escolha a Operação")
    estado.valorIput1 = '';
    estado.valorIput2 = '';
  }  
    return estado.operacao = oper.target.value
 }

function valorDigitado1(n1){
  let valor = parseInt(n1.target.value)
  if(estado.operacao == ''){
    alert("Escolha a Operação")
    estado.valorIput1 = '';
    estado.valorIput2 = '';
  }
  return valor;

}

function valorDigitado2(n2){
  let valor = parseInt(n2.target.value)
  if(estado.operacao == ''){
    alert("Escolha a Operação")
    estado.valorIput1 = '';
    estado.valorIput2 = '';
  }
  
 return valor, valorOperado();
}

function valorOperado(operacao, n1, n2 ){
  operacao = estado.operacao;
  n1 = estado.valorIput1
  n2 = estado.valorIput2

  estado.valorIput1 = ''
  estado.valorIput2 = ''

  switch(operacao){
      case "Soma" :
      return estado.valor = n1 + n2
    
      case "Subtracao" :
      return estado.valor = (n1 - n2)
      
      case "Multiplicacao" :
      return estado.valor = n1 * n2
      
      case "Divisao" :
      return estado.valor = n1 / n2

      default:
        estado.valor
  }
}


</script>

<template>
  <header>
    <div class="logo">
      <img alt="Vue logo" src="./assets/logo.svg" width="50" height="50" />
      <h1>Exercício vue modulo 27</h1>
    </div>
  </header>

  <body>
    <div class="container">
      <section class="section__resultado">
            <h3 v-if="estado.operacao != ''">{{ estado.textoInicial + estado.operacao }}</h3>
            <h3 v-if="estado.valor > 0">Resultado da Operação é:</h3>
            <span>{{ estado.valor }}</span>
      </section>

      <section class="section__operacao">
                <h3>Escolha a Operção</h3>
                    <select @change="opEscolhida($event)" v-model="estado.operacao">
                     <option value="Soma">Soma</option>
                     <option value="Subtracao">Subtracão</option>
                     <option value="Multiplicacao">Multiplicacão</option>
                     <option value="Divisao">Divisão</option>
                  </select>
        </section>

          <section class="section__valor">
            <label>Digite o Primeiro Valor</label>
            <div>
              <input @keyup="valorDigitado1" v-model="estado.valorIput1" type="number">
            </div>
            <label>Digite o Segundo Valor</label>
            <div>
              <input @keyup="valorDigitado2" v-model="estado.valorIput2" type="number">
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
}


.section__valor input{
  padding: 4px;
  margin-bottom: 16px;
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
