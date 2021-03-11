<template>
  <table>
  <thead>
    <tr>
      <th>Domínio</th>
      <th>E-mails</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="d in lista" :key="d['domain']">
      <td>{{ d['domain'] }}</td>
      <td>
        <p v-for="e in d['emails']" :key='e'>{{ e }}</p>
      </td>
    </tr>
  </tbody>
  </table>
</template>

<script>
export default {
  name: 'Tabela',
  props: {
    lista: Array
  }
}
</script>

<style scoped>

table, th, td {
  border: 1px solid black;
  padding: 0.5rem;
}

table {
  margin: 0 auto;
  border-collapse: collapse;
  width: 100%;
}

th {
  text-align: left;
}

td {
  vertical-align: baseline;
  margin: 1rem;
}

tbody tr:nth-child(odd) {
  background: #eee;
}

</style>
