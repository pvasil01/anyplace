<template>
  <option><slot></slot></option>
</template>
<!-- TODO REname space
- have variable: type functoin: isBuilding isVessel
- return dynamic icon based on type

- SEPARTE class:
-- name Space (pure TS / Typescript)
-- coordiantes_lat... coord_lon, buid, name
-->

<script>
export default {
  name: "building",
/*
  props: {
    coordinates_lat:null,
    name:null,
    buid:null,
    coordinates_lon:null,
    is_published:null,
    space_type:null
  },
  */
  data() {
    return {
      // space of Type:Space
    coordinates_lat: null,
      name: null,
      buid: null,
      coordinates_lon: null,
      is_published: null,
      space_type: null
    }
  },
  methods: {
    getLon: function() {
      return this.coordinates_lon;
},

    getLat: function() {
      return this.coordinates_lat;
    }
  }

}
</script>

<style scoped>

</style>