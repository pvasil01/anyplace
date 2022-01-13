<template>

  <button id="button-menu-left" class="input-group-text bg-white" @click="showMenu"><i class="fas fa-bars" ></i></button>
  <div id="menu-left" ref="menu-left" class="menu-off menu-appearance">
    <div class="d-flex justify-content-between pt-3">
      <h3 class="fw-bold align-self-center font-monospace">Architect</h3>
      <button @click="hideMenu" id="button-close-menu-left" class="btn-close" aria-label="Close"></button>
    </div>
    <hr class="pt-0 text-muted">
    <div class="d-flex justify-content-start pt-1 d-grid gap-2 col mx-auto">
      <button class="btn bg-white btn-hover-color"><i class="fas fa-map-marker-alt me-3"></i>
        Your location sharing
      </button>
    </div>
    <div class="d-flex justify-content-start d-grid gap-2 col mx-auto">
      <button class="btn bg-white btn-hover-color"><i class="far fa-bookmark me-3"></i>
        Your places
      </button>
    </div>
    <div class="d-flex justify-content-start d-grid gap-2 col mx-auto">
      <button class="btn bg-white btn-hover-color"><i class="fas fa-route me-3"></i>
        Your timeline
      </button>
    </div>
    <div class="d-flex justify-content-start d-grid gap-2 col mx-auto">
      <button class="btn bg-white btn-hover-color"><i class="far fa-star me-3"></i>
        Favourites
      </button>
    </div>
    <hr class="pt-0 text-muted">
    <div class="d-flex justify-content-start d-grid gap-2 col mx-auto">
      <button class="btn bg-white btn-hover-color"><i class="fas fa-link me-3"></i>
        Share or embed map
      </button>
    </div>
    <div class="d-flex justify-content-start d-grid gap-2 col mx-auto">
      <button class="btn bg-white btn-hover-color"><i class="fas fa-print me-3"></i>
        Print
      </button>
    </div>
    <div class="d-flex justify-content-start d-grid gap-2 col mx-auto">
      <button class="btn bg-white btn-hover-color">
        Edit map
      </button>
    </div>
    <hr class="pt-0 text-muted">
    <div class="d-flex justify-content-start d-grid gap-2 col mx-auto">
      <button class="btn bg-white btn-hover-color">
        Tips and tricks
      </button>
    </div>
    <div class="d-flex justify-content-start d-grid gap-2 col mx-auto">
      <button class="btn bg-white btn-hover-color">
        Get help
      </button>
    </div>
    <hr class="pt-0 text-muted">
    <div class="d-flex justify-content-start d-grid gap-2 col mx-auto">
      <button class="btn bg-white btn-hover-color">
        Language
        <i class="fas fa-language"></i></button>
    </div>
    <div class="d-flex justify-content-start d-grid gap-2 col mx-auto">
      <button class="btn bg-white btn-hover-color">
        Maps activity
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "menu-left",
  data() {
    return {
      isShown:false
    }
  },
  methods: {
    showMenu(){
      console.log("before button was clicked to open  was set to  " +this.isShown)

       this.isShown=true;
      console.log("clicked the button to open menu and now it is se to  " +this.isShown)
      this.$refs["menu-left"].style.display="block"

    },
    hideMenu(){
      console.log("before button was clicked to hide  was set to  " +this.isShown)

      this.isShown=false;
      console.log("clicked the button to close menu and now it is se to  " +this.isShown)
      this.$refs["menu-left"].style.display="none"

    }

  }
}
</script>

<style scoped>

</style>