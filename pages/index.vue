<template>
  <div class="mainmenu">
    <h1 class="title">
      summer-hackathon2020
    </h1>
    <!-- <div class="container">
      <div>
        <Logo />
        
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
    <div class="wrapper">
      <div class="fakeLogin">
        <fakelogin />
      </div>
      <div class="instruction">
        <instruction />
      </div>
      <!-- <div class="miniTimer">
        <minitimer />
      </div> -->
      <div class="idList">
        <idlist />
      </div>
    </div>
  </div>
</template>

<script>
//コンポーネントインポート
import fakelogin from "~/components/fakeLogin";
import idlist from "~/components/idList";
import instruction from "~/components/instruction";
import minitimer from "~/components/miniTimer";

export default {};
</script>

<style>
.mainmenu {
  /* column-count: 2;
  column-gap: 2; */
  height: 500px;
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
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
    "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 30px;
  color: #35495e;
  letter-spacing: 1px;
  margin-left: 15px;
  margin-bottom: 15px;
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
.wrapper {
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: 200px 200px;
  grid-gap: 10px;
}
.fakeLogin {
  grid-column: 1;
  grid-row: 1 / 3;
}
</style>
