<script setup>
  const route = useRoute();
  const { data } = await useFetch('/api/ticker?id=' + route.params.id, { initialCache: false });
  const coin = reactive(data.value[0]);
</script>

<template>
  <div v-if="coin">
    <h2>{{ coin.name }} Detail page</h2>
    <table border="1 px solid">
      <thead>
        <th>Symbol</th>
        <th>Rank</th>
        <th>Price - US $</th>
        <th>Market Cap - US $</th>
      </thead>
      <tr>
        <td>{{ coin.symbol }}</td>
        <td>{{ coin.rank }}</td>
        <td>{{ coin.price_usd }}</td>
        <td>{{ coin.market_cap_usd }}</td>
      </tr>
    </table>
  </div>
  <div v-else>
    <h2>No data coin available</h2>
  </div>
</template>