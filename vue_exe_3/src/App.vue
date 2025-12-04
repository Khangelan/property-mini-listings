<template>
  <div class="app">
    <HeaderBar :total="filteredProperties.length" />

    <div class="controls">
      <input v-model="searchQuery" placeholder="Search by title or location..." />
      <select v-model="sortOrder">
        <option value="asc">Price: Low to High</option>
        <option value="desc">Price: High to Low</option>
      </select>
    </div>

    <PropertyList 
      :properties="filteredAndSortedProperties" 
      @toggle-bookmark="toggleBookmark"
    />
  </div>
</template>

<script>
import HeaderBar from './icons/HeaderBar.vue'
import PropertyList from './icons/PropertyList.vue'

export default {
  name: 'App',
  components: { HeaderBar, PropertyList },
  data() {
    return {
      searchQuery: '',
      sortOrder: 'asc',
      properties: [
        { id: 1, title: 'Modern Apartment', location: 'Cape Town', price: 1200, type: 'Apartment', image: 'https://via.placeholder.com/300', available: true, bookmarked: false },
        { id: 2, title: 'Beach House', location: 'Durban', price: 2500, type: 'House', image: 'https://via.placeholder.com/300', available: false, bookmarked: false },
        { id: 3, title: 'City Loft', location: 'Johannesburg', price: 950, type: 'Loft', image: 'https://via.placeholder.com/300', available: true, bookmarked: false }
      ]
    }
  },
  computed: {
    filteredProperties() {
      return this.properties.filter(p =>
        p.title.toLowerCase().includes(this.searchQuery.toLowerCase()) ||
        p.location.toLowerCase().includes(this.searchQuery.toLowerCase())
      )
    },
    filteredAndSortedProperties() {
      return [...this.filteredProperties].sort((a, b) =>
        this.sortOrder === 'asc' ? a.price - b.price : b.price - a.price
      )
    }
  },
  methods: {
    toggleBookmark(id) {
      const property = this.properties.find(p => p.id === id)
      if(property) property.bookmarked = !property.bookmarked
    }
  }
}
</script>

<style>
.app { max-width: 900px; margin: auto; font-family: Arial, sans-serif; }
.controls { display: flex; gap: 10px; margin: 15px 0; }
.controls input, .controls select { flex: 1; padding: 8px; }
</style>
