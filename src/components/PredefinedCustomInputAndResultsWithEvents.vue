<template>
  <div>
    <google-places-autocomplete
      @resultChanged="placeDetail => place = placeDetail"
      @resultCleared="() => place = null"
      value="London, UK"
      :place="defaultPlace"
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
          class="p-4 w-full max-w-sm outline-none rounded-t-lg"
          placeholder="Type something ..."
          autocomplete="off"
        >
      </div>

      <span slot="item" slot-scope="{ place }" class="block p-2">
        {{ place.description }}
      </span>
      <span slot="activeItem" slot-scope="{ place }" class="block p-2 rounded bg-green-lightest font-bold">
        {{ place.description }}
      </span>
    </google-places-autocomplete>

    <h3 class="mt-8 text-grey-dark" v-if="place">Result</h3>
    <pre v-html="place" class="text-xs" />
  </div>
</template>

<script>
import { GooglePlacesAutocomplete } from 'vue-better-google-places-autocomplete'

export default {
  name: 'PredefinedCustomInputAndResultsWithEvents',
  components: {
    GooglePlacesAutocomplete,
  },
  data() {
    return {
      place: null,
    }
  },
  computed: {
    defaultPlace() {
      return {"address_components":[{"long_name":"London","short_name":"London","types":["locality","political"]},{"long_name":"London","short_name":"London","types":["postal_town"]},{"long_name":"Greater London","short_name":"Greater London","types":["administrative_area_level_2","political"]},{"long_name":"England","short_name":"England","types":["administrative_area_level_1","political"]},{"long_name":"United Kingdom","short_name":"GB","types":["country","political"]}],"adr_address":"<span class=\"locality\">London</span>, <span class=\"country-name\">UK</span>","formatted_address":"London, UK","geometry":{"location":{"lat":{"_custom":{"type":"function","display":"<span>ƒ</span> ()"}},"lng":{"_custom":{"type":"function","display":"<span>ƒ</span> ()"}}},"viewport":{"ma":{"j":51.38494009999999,"l":51.6723432},"ga":{"j":-0.351468299999965,"l":0.14827100000002247}}},"icon":"https://maps.gstatic.com/mapfiles/place_api/icons/geocode-71.png","id":"b1a8b96daab5065cf4a08f953e577c34cdf769c0","name":"London","photos":[{"height":1200,"html_attributions":["<a href=\"https://maps.google.com/maps/contrib/114647298085396208768/photos\">George Morina</a>"],"width":1600,"getUrl":{"_custom":{"type":"function","display":"<span>ƒ</span> (g)"}}},{"height":1920,"html_attributions":["<a href=\"https://maps.google.com/maps/contrib/113856488991850624540/photos\">Franz Baernthaler</a>"],"width":2560,"getUrl":{"_custom":{"type":"function","display":"<span>ƒ</span> (g)"}}},{"height":514,"html_attributions":["<a href=\"https://maps.google.com/maps/contrib/104494000466617447205/photos\">Manju Gupta</a>"],"width":770,"getUrl":{"_custom":{"type":"function","display":"<span>ƒ</span> (g)"}}},{"height":809,"html_attributions":["<a href=\"https://maps.google.com/maps/contrib/117764516527474292201/photos\">Alex Teixeira</a>"],"width":1080,"getUrl":{"_custom":{"type":"function","display":"<span>ƒ</span> (g)"}}},{"height":800,"html_attributions":["<a href=\"https://maps.google.com/maps/contrib/116096154494220703851/photos\">Владимир Боков</a>"],"width":1280,"getUrl":{"_custom":{"type":"function","display":"<span>ƒ</span> (g)"}}},{"height":3672,"html_attributions":["<a href=\"https://maps.google.com/maps/contrib/112970828110885182166/photos\">Susana Carbajales</a>"],"width":4896,"getUrl":{"_custom":{"type":"function","display":"<span>ƒ</span> (g)"}}},{"height":866,"html_attributions":["<a href=\"https://maps.google.com/maps/contrib/112793786414835308942/photos\">Enrico Presotto</a>"],"width":1379,"getUrl":{"_custom":{"type":"function","display":"<span>ƒ</span> (g)"}}},{"height":1452,"html_attributions":["<a href=\"https://maps.google.com/maps/contrib/109648577636572315039/photos\">Leslie</a>"],"width":5248,"getUrl":{"_custom":{"type":"function","display":"<span>ƒ</span> (g)"}}},{"height":1016,"html_attributions":["<a href=\"https://maps.google.com/maps/contrib/114647298085396208768/photos\">George Morina</a>"],"width":1600,"getUrl":{"_custom":{"type":"function","display":"<span>ƒ</span> (g)"}}},{"height":1080,"html_attributions":["<a href=\"https://maps.google.com/maps/contrib/111050241231844820150/photos\">Cristina Cunsolo</a>"],"width":1920,"getUrl":{"_custom":{"type":"function","display":"<span>ƒ</span> (g)"}}}],"place_id":"ChIJdd4hrwug2EcRmSrV3Vo6llI","reference":"ChIJdd4hrwug2EcRmSrV3Vo6llI","scope":"GOOGLE","types":["locality","political"],"url":"https://maps.google.com/?q=London,+UK&ftid=0x47d8a00baf21de75:0x52963a5addd52a99","utc_offset":60,"vicinity":"London","html_attributions":[]}
    }
  }
}
</script>

<style>
.vbga-results {
  @apply .list-reset w-full max-w-sm p-4 bg-white border-t rounded-b-lg;
}
</style>
