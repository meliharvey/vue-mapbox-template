<template>
  <div class="home">
    <MglMap
      :accessToken="accessToken"
      :mapStyle="mapStyle"
      @load="onMapLoaded"
    >
    <MglNavigationControl position="top-right"/>
    <MglGeolocateControl position="top-right" />
    </MglMap>
  </div>
</template>

<script>
// @ is an alias to /src
import Mapbox from "mapbox-gl";
import { MglMap, MglNavigationControl, MglGeolocateControl } from "vue-mapbox";

export default {
  name: "home",
  components: {
    MglMap,
    MglNavigationControl,
    MglGeolocateControl
  },
  data() {
    return {
      accessToken: process.env.VUE_APP_MAPBOX_API_KEY, // your access token from your mapbox account
      mapStyle: "mapbox://styles/mapbox/basic-v9", // your map style
    };
  },
  created() {
    // We need to set mapbox-gl library here in order to use it in template
    this.mapbox = Mapbox;
    this.map = null;
  },
  mounted() {
    console.log(process.env)
  },
  methods: {
    onMapLoaded(event) {
      // in component
      this.map = event.map;
    }
  }
};
</script>

<style lang="scss">
.home {
  height: calc(100vh - 60px);
}
</style>
