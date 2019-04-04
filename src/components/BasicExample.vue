<template>
  <div>
    <google-places-autocomplete />
  </div>
</template>

<script>
import { GooglePlacesAutocomplete } from 'vue-better-google-places-autocomplete'

export default {
  name: 'BasicExample',
  components: {
    GooglePlacesAutocomplete,
  },
}
</script>
