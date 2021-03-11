<template>
  <h1>Lista de contatos por Domínio</h1>
  <div class="container">
    <Tabela :lista="data"/>
  </div>
  
</template>

<script>
import Tabela from './components/Tabela.vue'
import json from './data.json'
import Chart from 'chart.js';

export default {
  name: 'App',
  components: {
    Tabela
  },
  setup() {
    const data = json['data']
    // let grafico = []
    let emails_grafico = []
    let domain_grafico = []

    emails_grafico = data.map(function (d) {
      return [ d['emails'].length ]
    })

    domain_grafico = data.map(function (d) {
      return [ d['domain'] ]
    })

    const ctx = document.getElementById('grafico');
    const grafico = new Chart(ctx, {
      type: 'doughnut',
      data: {
          datasets: [{
              data: emails_grafico,
              backgroundColor: [
                'rgba(255, 99, 132)',
                'rgba(54, 162, 235)',
                'rgba(255, 206, 86)',
                'rgba(75, 192, 192)',
                'rgba(153, 102, 255)',
                'rgba(255, 159, 64)']
          }],
          labels: domain_grafico,
      },
      options: { responsive: true }
    });

    return { data, grafico }
  },
}
</script>

<style>
* {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1rem;
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

h1 {
  text-align: center;
  padding: 2rem;
}

.container {
  width: 50%;
  margin: 0 auto;
}
</style>
