<template>
  <div 
    id="home" 
    :class="desktop ? 'home-desktop' : 
            mobile ? 'home-mobile' : 
            'home-default'"
  >
    <div id="topSection">
      <div class="top-section">
        <!-- <button class="btn btn-round">Check out our new jobs available </button> -->
        <h1 class="top-section-header">UX Network</h1>
        <h1 class="top-section-h1">Programmable Liquidity</h1>
        <p class="top-section-p">A hybrid algorithmic unit of account with network transactional dynamics driving decentralised monetary policy.</p>
        <button class="btn1">Get UXX</button>
        <button class="btn2">Learn</button>
        <div>
          <img src="@/assets/images/dials.png" alt="" class="dials-image">
        </div>
      </div>
      <img src="@/assets/images/infinitebubble.webp" alt="" class="infinite-image" loading="lazy">
    </div>

    <div id="economicModel" :class="width < 1600 ? 'economicModel' : ''" >
      <img v-if="width<1060" src="@/assets/images/uxxcoin-wide.png" class="economicModel-image">
      <img v-else src="@/assets/images/uxxcoin.png">
      <div :class="width < 1060 ? 'economical-hybrid' : 'hybrid'">
        <h2>A HYBRID STABLE COIN</h2>
        <p>UXX is an innovative algorithmic and uncollateralised token with no defined exogenous peg, no stabilisation requirements, and no fees</p>
        <h4>THE PRECISION OF DECOMPOSITION<img src="@/assets/images/arrowBox.png"></h4>
      </div>
    </div>

    <div id="tokenomics" :class="!desktop ? 'tokenomics-desktop' : ''"> 
      <div class="grid">
        <div>
          <h3>SUMMARY</h3>
        </div>
        <div 
          v-for="item in grid"
          :key="item.label"
          @mouseover="gridLabel=item.label"
          @click="gridLabel=item.label"
          :class="item.label==gridLabel ? `tech cursor`:'cursor'"
        >
          <img :src="gridLink(item)" :class="item.label==gridLabel ? 'gridItemImage':''">
          <div>{{item.label}}</div>
        </div>
      </div>
      <div class="desktop-right" v-if="desktop" >
        <img src="@/assets/images/des3.png">
        <div class="desktop-top-right">
          <img class="gridItemImage desktop-grid-iamge" :src="gridLink(gridItem)">
          <h4 class="gridItem-h4">{{gridItem.label}}</h4>
          <p class="gridItem-p">{{gridItem.text}}</p>
        </div>
      </div>
    </div>

    <div class="learn-about">
      <div class="learn-div"></div>
      <h3 class="learn">Learn</h3>
      <h3 class="learn">About UXX app</h3>
    </div>

    <div id="charts">
      <div>
        <img class="charts-image" :src="'/charts/'+charts[cIndex]+'.png'" :srcset="'/charts/'+charts[cIndex]+'.png 1x,/charts/'+ charts[cIndex] +'@2x.png 2x'">
      </div>
      <div :class="width < 1000 ? 'top-left0 arrow' : 'left17 arrow'"
        @click="charts[cIndex-1] ? cIndex-- : cIndex=charts.length-1" class="arrow">
        <div class="border-right"/></div>
      <div :class="width < 1000 ? 'top100 arrow right-0' : 'arrow right-0'" @click="charts[cIndex+1] ? cIndex++ : cIndex=0"><div class="border-left" /></div>
    </div>
    
    <div class="uxx-info">
      <div id="uxxInfo">
        <div class="uxx-div"></div>
        <h2 class="uxx-h2">UXX: THE FIRST OF ITS KIND HYBRID-STABLE COIN</h2>
        <div class="uxx-h2-div">

          <p class="uxx-p-bold">The monetary policy and token emission of UXX is determined by the liquidity requirements of its individual users.</p>
          <p class="uxx-p-top34">UXX is a constructed as a stablecoin with infinite issuance yet with no defined fixed price peg. Rather than reference an external currency or asset, the model allows the peg to be resolved from the UXX market itself through the dynamic liquidity and associated transactional velocity</p>
          <p class="uxx-p-top30">Since UXX naturally reflects the network economy it becomes a natural choice as a conduit unit of account and a base asset for open finance vertical models. With no fees or value- trap mechanisms, UXX enables a seamless circular economic flow back through the network itself.</p>
        </div>
        <img class="uxx-info-image" src="@/assets/images/stat3.png" srcset="@/assets/images/stat3.png 1x, @/assets/images/stat3@2x.png 2x" alt="">
      </div>
    </div>

    <div class="stay-div">
      <div class="stay-flex">
        <img src="@/assets/images/bottom.gif" class="stay-flex-max" loading="lazy">
        <div id="linksBottom">
          <h3 class="stay-h3">STAY IN TOUCH</h3>
          <div>..</div>
          <div>info@uxx.network></div>
          <div> <img src="@/assets/images/telegram.png"> ...</div>
          <div><img src="@/assets/images/discord.png">...</div>
          <button class="stay-margin-top">Send Email</button>

        </div>
      </div>
    </div>

    <div id="footer">
      <div>
        <span href="#">ABOUT</span>
        <span href="#">SUMMARY</span>
        <span href="#">UXX C All Rights Reserved</span>
      </div>
      <span>Developed by</span>
    </div>

  </div>
  
</template>

<script>
// @ is an alias to /src
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
  name: 'Home',
  data(){
    return{
      width:window.innerWidth,
      grid:[
        {
          label:"staking",
          text:""
        },
        {
          label:"unstaking",
          text:""
        },
        {
          label:"no fees",
          text:""
        },
        {
          label:"single token",
          text:""
        },
        {
          label:"governance",
          text:""
        },
        {
          label:"mining",
          text:""
        },
        {
          label:"unpegged stablecoin",
          text:"The UXX model allows the classic stablecoin peg to be resolved internally by the network through the balance of system liquidity and transactional velocity"
        },
        {
          label:"monetary policy" ,
          text:""
        }
      ],
      gridLabel: "unpegged stablecoin",
      charts:['evenmedium', 'shortbias', 'longbias', 'evenhigh'],
      cIndex:0,
    }
  },
  computed:{
    gridItem: s => s.grid.find(item=>item.label==s.gridLabel),
    desktop:s=>s.width>1122,
    mobile:s=>s.width<771,
  },
  methods:{
    gridLink(item){
      return '/summary/' + item.label.replace(' ', '') + '.svg'
    },
    updateDimensions(e){
      this.width = window.innerWidth;
    },
  },
  mounted(){
    window.addEventListener('resize',throttle(this.updateDimensions),true);
  },
  components: {
  }
}
</script>

<style>
  @import url('../assets/css/Home.css');
</style>