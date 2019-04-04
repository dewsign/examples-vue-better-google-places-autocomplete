<template>
  <div>
    <google-places-autocomplete
      @resultChanged="placeDetail => place = placeDetail"
      @resultCleared="() => place = null"
    />

    <h3 class="mt-8 text-grey-dark" v-if="place">Result</h3>
    <pre v-html="place" class="text-xs" />
  </div>
</template>

<script>
import { GooglePlacesAutocomplete } from 'vue-better-google-places-autocomplete'

export default {
  name: 'WithEvents',
  components: {
    GooglePlacesAutocomplete,
  },
  data() {
    return {
      place: null,
    }
  },
}
</script>
