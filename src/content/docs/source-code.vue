<template>
  <div><h1 id=source-code>Source Code</h1>
<p>Develop on Tendermint&#x2019;s open source platform. Start learning with <router-link to=/docs/guides/app-development>the guide</router-link></p>
<ul>
  <li><a href=http://github.com/tendermint/tendermint/wiki>
    <h4>Tendermint Spec</h4>
    <p>Get an overview of Tendermint&#x2019;s structure, algorithms, and roadmap.</p>
  </a></li>
  <li><a href=https://github.com/tendermint/tendermint>
    <h4>Tendermint Core</h4>
    <p>Tendermint Core</p>
  </a></li>
  <li><a href=https://github.com/tendermint/abci>
    <h4>ABCI</h4>
    <p>Tendermint socket protocol for blockchain applications</p>
  </a></li>
  <li><a href=https://github.com/tendermint/mintnet>
    <h4>Mintnet</h4>
    <p>Developer tool for deploying a Tendermint testnet</p>
  </a></li>
  <li><a href=https://github.com/tendermint/go-p2p>
    <h4>Go-P2P</h4>
    <p>Extensible P2P networking stack</p>
  </a></li>
  <li><a href=https://github.com/tendermint/go-merkle>
    <h4>Go-Merkle</h4>
    <p>Merkle hash trees for blocks and application state</p>
  </a></li>
  <li><a href=https://github.com/tendermint/go-wire>
    <h4>Go-Wire</h4>
    <p>Binary and JSON encoding/decoding</p>
  </a></li>
</ul>
</div>
</template>

<script>
export default {
  name: 'page-docs-entry',
  mounted () {
    document.title = 'Source Code - Documentation - Tendermint'
  }
}
</script>
