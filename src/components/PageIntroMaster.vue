<template>
<div class="master" v-bind:class="{ 'mobile-active': isActive, 'mobile-inactive': !isActive }" @click="toggleManual">
  <nav>
  <div class="title">Index</div>
  <router-link :to="'/intro'" exact>Introduction</router-link>
  <router-link :to="'/intro/abci-overview'">ABCI Overview</router-link>
  <router-link :to="'/intro/consensus-overview'">Consensus Overview</router-link>
  <router-link :to="'/intro/tendermint-vs-x'">Tendermint vs X</router-link>
  <div class="title">Getting Started</div>
  <router-link :to="'/intro/getting-started/download-tendermint'">1. Download Tendermint</router-link>
  <router-link :to="'/intro/getting-started/first-abci-app'">2. First ABCI App</router-link>
  <router-link :to="'/intro/getting-started/deploy-testnet'">3. Deploy Testnet</router-link>
  <router-link :to="'/intro/getting-started/next-steps'">4. Next Steps</router-link>
</nav>
  <btn-thumb v-show="isActive" icon="close"></btn-thumb>
  <btn-thumb v-show="!isActive" icon="bars"></btn-thumb>
</div><!--master-->
</template>

<script>
import $ from 'jquery'
import BtnThumb from './BtnThumb'

export default {
  name: 'page-docs-master',
  components: {
    BtnThumb
  },
  data () {
    return {
      isActive: false
    }
  },
  methods: {
    toggleAutomatic () {
      let self = this
      if ($(window).width() >= 720) self.isActive = true
      else self.isActive = false
    },
    toggleManual () {
      if ($(window).width() < 720) {
        this.isActive = !this.isActive
      }
    }
  },
  mounted () {
    this.toggleAutomatic()
    $(window).resize(() => this.toggleAutomatic())
  }
}
</script>
