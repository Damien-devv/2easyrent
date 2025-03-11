<script setup lang="ts">
import { defineProps } from 'vue'

defineProps<{
  property: {
    title: string
    description: string
    price: number
    location: string
    image: string
    bedrooms: number
    bathrooms: number
  }
}>()
</script>

<template>
  <div class="property-card">
    <img :src="property.image" :alt="property.title" class="property-image" />
    <div class="property-details">
      <h3 class="property-title">{{ property.title }}</h3>
      <p class="property-location">{{ property.location }}</p>
      <p class="property-price">${{ property.price.toLocaleString() }}/mo</p>
      <p class="property-description">{{ property.description }}</p>
      <div class="property-features">
        <span>{{ property.bedrooms }} BR</span>
        <span>{{ property.bathrooms }} BA</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
.property-card {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.2s;
}

.property-card:hover {
  transform: translateY(-5px);
}

.property-image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.property-details {
  padding: 1rem;
}

.property-title {
  margin: 0;
  font-size: 1.25rem;
  color: #213547;
}

.property-location {
  margin: 0.5rem 0;
  color: #666;
}

.property-price {
  margin: 0.5rem 0;
  font-size: 1.1rem;
  font-weight: bold;
  color: #213547;
}

.property-description {
  margin: 0.5rem 0;
  color: #444;
}

.property-features {
  display: flex;
  gap: 1rem;
  margin-top: 1rem;
  color: #666;
}
</style>
