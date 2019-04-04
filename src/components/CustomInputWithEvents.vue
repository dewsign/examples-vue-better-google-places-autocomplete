<template>
  <div>
    <google-places-autocomplete
      @resultChanged="placeDetail => place = placeDetail"
      @resultCleared="() => place = null"
    >
      <div slot="input" slot-scope="{ context, events, actions }">
        <label for="locationInput" class="block my-4 text-xl text-grey-dark">Address Search</label>
        <input
          v-model="context.input"
          @focus="events.inputHasReceivedFocus"
          @input="events.inputHasChanged"
          @keydown.enter.prevent="actions.selectItemFromList"
          @keydown.down.prevent="actions.shiftResultsSelection"
          @keydown.up.prevent="actions.unshiftResultsSelection"
          type="search"
          id="locationInput"
          class="p-4 w-full max-w-sm outline-none"
          placeholder="Type something ..."
        >
      </div>
    </google-places-autocomplete>

    <h3 class="mt-8 text-grey-dark" v-if="place">Result</h3>
    <pre v-html="place" class="text-xs" />
  </div>
</template>

<script>
import { GooglePlacesAutocomplete } from 'vue-better-google-places-autocomplete'

export default {
  name: 'CustomInputWithEvents',
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
