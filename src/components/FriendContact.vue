<template>
  <li>
    <h2>{{ name }} {{ isFavorite ? '(Favorite)' : '' }}</h2>
    <button @click="toggleFavorite(id)">Toggle Favorite</button>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong> {{ phoneNumber }}</li>
      <li><strong>Email:</strong> {{ emailAddress }}</li>
    </ul>

    <button @click="$emit('delete-friend', this.id)">Delete</button>
  </li>
</template>

<script>
export default {
  data() {
    return {
      detailsAreVisible: false,
    }
  },
  methods: {
    toggleFavorite() {
      this.$emit('toggle-favorite', this.id)
    },
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible
    },
  },
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavorite: {
      type: Boolean,
      default: false,
    },
  },
  emits: {
    'toggle-favorite': function (id) {
      if (!id) {
        console.warn('Id is missing')
        return false
      }

      return true
    },
    'delete-friend': function (id) {
      if (!id) {
        console.warn('Id is missing')
        return false
      }

      return true
    },
  },
}
</script>
