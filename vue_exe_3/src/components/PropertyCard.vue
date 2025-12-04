<template>
  <div class="card">
    <img :src="property.image" alt="" />
    <h3>{{ property.title }}</h3>
    <p>{{ property.location }}</p>
    <p>R {{ property.price.toLocaleString() }}</p>
    <span>{{ property.type }}</span>

    <div v-if="!property.available" class="badge">Not Available</div>

    <button @click="$emit('toggle-bookmark')" :class="{ bookmarked: property.bookmarked }">
      {{ property.bookmarked ? '★' : '☆' }}
    </button>
  </div>
</template>

<script>
export default {
  name: 'PropertyCard',
  props: { property: Object }
}
</script>

<style>
.card { position: relative; padding: 10px; border: 1px solid #ccc; border-radius: 8px; }
.badge { position: absolute; top: 10px; right: 10px; background: red; color: white; padding: 2px 6px; border-radius: 4px; font-size: 12px; }
button { margin-top: 10px; background: none; border: none; font-size: 18px; cursor: pointer; }
button.bookmarked { color: gold; }
</style>
