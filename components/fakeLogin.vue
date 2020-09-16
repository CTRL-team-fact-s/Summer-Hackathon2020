<template>
  <div>
    <h1>fakeLogin</h1>
    <el-input placeholder="番号を入力してください" v-model="input"></el-input>
    <el-input placeholder="パスワードを入力してください" v-model="input" show-password></el-input>
  </div>
</template>
<script>
export default {
  data() {
    return {
      input: ''
    }
  }
}
</script>