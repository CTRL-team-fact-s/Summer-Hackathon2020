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
function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min)) + min; //The maximum is exclusive and the minimum is inclusive
}
let password;
let limitcount;
function startGame() {
  for (let i = 0; i < 30; i++) {
    password.push(getRandomInt(0, 20));
    limitcount.push(0);
  }
}
function check(index, pass) {
  limitcount[index] = limitcount[index] + 1;
  if(limitcount[index] > 3) {

  } else {
    if(password[index] == pass) {

    } else {
      
    }
  }
}

</script>