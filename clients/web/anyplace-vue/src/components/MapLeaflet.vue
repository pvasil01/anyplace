<template>
  <div id="map"></div>
<!--
  <building v-for="building in places" :key="building" ></building>
-->

</template>

<script lang="ts">
import  { Options, Vue } from 'vue-class-component';

import "leaflet/dist/leaflet.css";
import L from "leaflet";
import building from "@/components/building.vue";
import Building from "@/components/building.vue";
import axios from "axios";

@Options({
  components: {Building},
  props: {
    msg: String,
    places: Array,
  },
  data() {
    return {
      map: null,
      spaces: []
    };
  },

 /* computed() {
    console.log("fetched spaces done.  Printed from leaflet component fetched #" + this.places.length);

    console.log("this is the entry of places at index 0" +  this.places[0].name)
    console.log("this is the coord lat of places at index 0" +  this.places[0].coordinates_lat)
    console.log("this is the coord lon of places at index 0" +  this.places[0].coordinates_lon)

  },
*/
  mounted() {
   // this.bindLeafletOSM(); // WAY1
     this.bindLeafletWithMapBox();  // WAY2
    // SHOW SPACES....
  },
  activated() {
      this.putMarker()
  },

  beforeDestroy() {
      if (this.map) {
        this.map.remove();
      }
    },
  created(){
  //  this.putMarker();




      axios
          .post('https://ap.cs.ucy.ac.cy:44/api/mapping/space/public',{})
          //   .then(data=>console.log(data.data.spaces))
          .then(data=> {
                this.spaces = data.data.spaces;
                console.log(data.data.spaces);
                // console.log(this.places);
                // LOG.D
                console.log("fetched spaces done. fetched  printing from leaflet #" + this.spaces.length);

                console.log("this is the entry of places at index 0 printing from leaflet " +  this.spaces[0].name)
                console.log("this is the coord lat of places at index 0 printing from leaflet " +  this.spaces[0].coordinates_lat)
                console.log("this is the coord lon of places at index 0 printing from leaflet " +  this.spaces[0].coordinates_lon)


            var marker = L.marker([51.5, -0.09]).addTo(this.map);
            marker.bindPopup("<b>Hello world!</b><br>I am a popup.").openPopup();
            //marker=L.marker([ this.spaces[0].coordinates_lat,this.spaces[0].coordinates_lon]).addTo(this.map);
           // marker.bindPopup("<b>Hello world!</b><br>I am a popup but this is a new marker ." + this.spaces[0].name);

            // ....

            for (let i=0; i<this.places.length; i++) {
               marker = L.marker([this.spaces[i].coordinates_lat, this.spaces[i].coordinates_lon]).addTo(this.map);
               marker.bindPopup("<b>Hello world!</b><br>I am a popup but this is a new marker ." + this.spaces[0].name);

            }

              }
          )
          .catch(err=>console.log(err))






  },
  methods: {
    bindLeafletOSM: function() {




      this.map = L.map('map').setView([51.959, -8.623], 12);
      L.tileLayer("http://{s}.tile.osm.org/{z}/{x}/{y}.png", {
        attribution:
            '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
      }).addTo(this.map);
    },
    bindLeafletWithMapBox: function() {
      const MAPBOX_TOKEN = process.env.VUE_APP_MAPBOX_TOKEN; // sign up: 'https://account.mapbox.com/access-tokens'
      this.map = L.map('map').setView([37.8496184,25.2963279], 3);
      L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token={accessToken}', {
        attribution: 'Map data &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Imagery © <a href="https://www.mapbox.com/">Mapbox</a>',
        maxZoom: 18,
        minZoom:2.5,
        id: 'mapbox/streets-v11',
        tileSize: 512,
        zoomOffset: -1,
        accessToken: MAPBOX_TOKEN
      }).addTo(this.map);
      var marker = L.marker([51.5, -0.09]).addTo(this.map);
      marker.bindPopup("<b>Hello world!</b><br>I am a popup.").openPopup();
      console.log("this is the markers langlot" + marker.getLatLng())
/*

      marker=L.marker([ this.spaces[0].coordinates_lat,this.spaces[0].coordinates_lon]).addTo(this.map);
      marker.bindPopup("<b>Hello world!</b><br>I am a popup but this is a new marker ." + this.spaces[0].name).openPopup();


*/

      /*  for (let i=0; i<this.places.length; i++) {
          var marker = L.marker([this.places[i].coordinates_lat, this.places[i].coordinates_lon]).addTo(this.map);

        }*/



    },

    putMarker: function (){
      //console.log("this is the entry of places at index 0" +  this.places[0])

      console.log("fetched spaces done.  Printed from leaflet component fetched #" + this.places.length);

      console.log("this is the entry of places at index 0" +  this.places[0].name)
      console.log("this is the coord lat of places at index 0" +  this.places[0].coordinates_lat)
      console.log("this is the coord lon of places at index 0" +  this.places[0].coordinates_lon)


    }
  },

})

export default class MapLeaflet extends Vue {
  msg!: string /** parameter accepted by the {@link MapLeaflet} class */
}
</script>

<!-- scoped: limits CSS to this component only -->
<style scoped lang="scss">
#map {
    width: 100vw;
    height: 100vh;
}
</style>
