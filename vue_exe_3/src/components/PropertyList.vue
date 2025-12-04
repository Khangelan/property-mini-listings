<template>
  <div class="property-grid">
    <PropertyCard 
      v-for="p in properties" 
      :key="p.id" 
      :property="p"
      @toggle-bookmark="$emit('toggle-bookmark', p.id)"
    />
  </div>
</template>

<script>
import PropertyCard from './PropertyCard.vue'

export default {
  name: 'PropertyList',
  components: { PropertyCard },
  props: { properties: Array }
}
</script>

<style>
.property-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr)); gap: 15px; }
</style>
