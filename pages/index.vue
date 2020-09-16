<template>
  <div class="mainmenu">
    <!-- <div class="container">
      <div>
        <Logo />
        
        <h1 class="title">
          summer-hackathon2020
        </h1>
        <div class="links">
          <a
            href="https://nuxtjs.org/"
            target="_blank"
            rel="noopener noreferrer"
            class="button--green"
          >
            Documentation
          </a>
          <a
            href="https://github.com/nuxt/nuxt.js"
            target="_blank"
            rel="noopener noreferrer"
            class="button--grey"
          >
            GitHub
          </a>
        </div>
      </div>
    </div> -->
    <div class="container">
      <fakeLogin />
    </div>
    <div class="subtitle">
      <idList />
    </div>
    <div class = "subtitle">
      <instruction />
    </div>
    <div>
      <miniTimer />
    </div>
  </div>
</template>

<script>//コンポーネントインポート
import fakeLogin from "~/components/fakeLogin";
import idList from "~/components/idList";
import instruction from "~/components/instruction";

import miniTimer from "~/components/miniTimer";

export default {}
</script>

<style>
.mainmenu {
  column-count: 2;
  column-gap: 0;
}

.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
