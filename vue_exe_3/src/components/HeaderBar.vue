<template>
  <header>
    <h1>Homes & Beyond</h1>
    <p>Total properties: {{ total }}</p>
  </header>
</template>

<script>
export default {
  name: 'HeaderBar',
  props: { total: Number }
}
</script>

<style>
header { text-align: center; margin-bottom: 15px; }
</style>
