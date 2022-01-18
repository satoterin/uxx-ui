<template>
  <div id="app">
    <header>
      <div id="nav">
        <router-link to="/" class="navbar">
          <img src="@/assets/images/logo.png" alt="">
          <div id="logoText">UXX</div>
        </router-link>
        <div class="links" v-show="width>1134" v-if="!$route.path.startsWith('/app')">
          <router-link to="/about">About</router-link>
          <router-link to="/summary">Summary</router-link>
          <router-link to="/resource">resource</router-link>
          <router-link to="/contact">contact</router-link>
          <router-link to="/system">system</router-link>
          <router-link to="/learn">learn</router-link>
        </div>
        <div class="links home" v-show="width>1134" v-else >
          <router-link to="/app">Home</router-link>
          <router-link to="/app/stake">stake</router-link>
          <router-link to="/app/mine">mine</router-link>
        </div>
      </div>
      <div id="social"> 
        <img src="@/assets/images/telegram.png" alt="">
        <img src="@/assets/images/discord.png" alt="">
        <router-link to="/app"><button to="/app" class="btn-app">App</button></router-link>
      </div>

    </header>
    <router-view/>
  </div>
</template>
<script>
const throttle = (func, limit=1) => {
  let inThrottle
  return function() {
    const args = arguments
    const context = this
    if (!inThrottle) {
      func.apply(context, args)
      inThrottle = true
      setTimeout(() => inThrottle = false, limit)
    }
  }
}
export default {
  data(){
    return{
      width:window.innerWidth,
    }
  },
  computed:{
    gridItem: s => s.grid.find(item=>item.label==s.gridLabel),
    desktop:s=>s.width>1122,
    mobile:s=>s.width<771,
  },
  mounted(){
    window.addEventListener('resize',throttle(this.updateDimensions),true);
    console.log(this.$route)
  },
  methods:{
    updateDimensions(e){ this.width = window.innerWidth; },
  },
}
</script>
<style>
  @import url('./assets/css/App.css');
</style>
