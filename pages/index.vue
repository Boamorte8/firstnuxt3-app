<script setup>
  const { data } = await useFetch('/api/tickers?limit=10');
</script>

<template>
  <div>
    <h1>Index Page</h1>

    <table border="1 px solid">
      <thead>
        <tr>
          <th>Name</th>
          <th>Symbol</th>
          <th class="highlight">Price</th>
          <th>Details</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="currency in data.data" :key="data.data.id">
          <td>{{ currency.name }}</td>
          <td>{{ currency.symbol }}</td>
          <td>{{ currency.price_usd }}</td>
          <td>
            <NuxtLink :to="'/currency/' + currency.id">{{ currency.id }}</NuxtLink>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
  .highlight {
    background-color: blue;
    color: white;
  }
</style>