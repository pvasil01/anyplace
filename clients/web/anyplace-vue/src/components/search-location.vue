<template>
  <!-- TODO rename search bar -->

<!--  <div v-for="building in filteredList" :key="building" v-text="building.name">
  </div>-->

<!--  <ul>
    <li v-for="building in filteredList" :key="building" v-text="building.name"> </li>
  </ul>-->

  <input id="input-search" ref="input-search"  @blur="handleBlur" type="text" class="form-control border-sides-none d-none d-lg-block"
         placeholder="Search" aria-label="Search" list="places">
        <datalist id="places" style="width: 100px">


<!--
       <option v-for="building in places" v-text="building.name" :key="building" :value="building"> </option>
-->
        <building v-for="building in places" v-text="building.name" :key="building" > </building>


        </datalist>
  <button id="button-search" v-on:click="searchButtonClicked" class="input-group-text bg-white">
    <i class="fas fa-search"></i>
  </button>

<!--
  <button v-on:click="filteredList" type="reset"> CLICK ME </button>-->




</template>

<script>
import {SCREEN_SIZE_MEDIUM} from "@/main";
import building from "@/components/building";

export default {
  name: "search-location",
  components: {building},
  data() {



    return {
      // UNIQUE ELEMENTS:
      /** search box. on mobile is hidden when not in use. */
      // TODOc.. others.. import from Home.vue
   //  elInputSearch: HTMLInputElement = this.$refs["input-search"] as HTMLInputElement,

      search: '',
    }

  },


  props: {
    places: Array,
  },

  methods: {
    isScreenMediumOrSmall() {
      return document.body.clientWidth < SCREEN_SIZE_MEDIUM
      // if (document.body.clientWidth < SCREEN_SIZE_MEDIUM){
      // TODO: LOG.D
      // class LOG: with methods: { LEVEL=2;
    //}
      // LOG.D1.. LOG.D2(msg)
      //    LOG.D3("The size of your screen is less than medium")
      //console.log("The size of your screen is less than medium")
      // }
    },
    isHiddenInputSearchOnMobile() {
      // return "input-search".classList.contains("d-none")
      // return this.check
      return this.$refs["input-search"].classList.contains("d-none")
    },
    showInputSearchOnMobile() {
      //return "input-search".classList.remove("d-none")
      //return
      this.$refs["input-search"].classList.remove("d-none")
    },
    hideInputSearchOnMobile() {
      // return "input-search".classList.add("d-none")
      // return  this.check=false;
      //return
      this.$refs["input-search"].classList.add("d-none")
    },

    handleBlur() { // focus out exmape... we talked..
      if (this.isScreenMediumOrSmall()) {
        this.hideInputSearchOnMobile()
      }
    },
    searchButtonClicked() {
      if (this.isScreenMediumOrSmall()) {
        if (this.isHiddenInputSearchOnMobile()) {
          this.showInputSearchOnMobile();
          this.$refs["input-search"].focus();

          //  elInputSearch.focus()
        } else {
          //  trySearch();

          this.hideInputSearchOnMobile() // optional..
        }
        //  } else { // large screens
        // trySearch();
      }
    },

     // SEARCH AUTOCOMPLETE LIST etc LATER!
    filteredList() {
      return this.places.filter((building) => {
        return building.name.match(this.search);
       // console.log(building.name.match(this.search))
      });

    }

    }


}
</script>

<style scoped>

</style>