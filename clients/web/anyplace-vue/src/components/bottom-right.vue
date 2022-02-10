<template>
  <!-- ACTION BUTTONS rename -->
  <div v-show="isShown" id="wrapper-actions" ref="wrappers-actions" class="btn-group-vertical" role="group">
    <button id="button1" class="btn mb-3 btn-light circle-icon" type="button">
      <i class="fas fa-map-marked-alt fa-2x"></i>
    </button>
    <button class="btn btn-light circle-icon" type="button" id="button2">
      <i class="fas fa-map-marker-alt fa-2x"></i>
    </button>
    <button class="btn btn-light mb-3 circle-icon my-2" type="button" id="button3">
      <i class="fas fa-route fa-2x"></i>
    </button>
    <button class="btn btn-light circle-icon" type="button" id="button4">
      <i class="fas fa-directions fa-2x"></i>
    </button>
  </div>
  <div class="d-flex justify-content-end my-2">
    <button @click="isShown= !isShown ; showButtons" id="button-toggle-actions" class="btn btn-primary circle-icon" type="button">
      <i ref="arrowButton" class="fas fa-angle-double-up fa-2x"></i>
    </button>
  </div>
</template>

<script>
export default {
  name: "bottom-right",
  data (){
    return {
      isShown:false
    }
  },
  methods: {


    showButtons() {


      if (!(this.isShown)){
        this.$refs["arrowButton"].classList.add("fa-angle-double-up")



      }
      else {
        this.$refs["arrowButton"].classList.add("fa-angle-double-down")



      }

      }


    }



}










</script>

<style scoped>

</style>