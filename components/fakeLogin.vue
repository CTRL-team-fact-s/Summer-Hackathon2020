<template>
  <div>
    <h1>fakeLogin</h1>
    <el-button :plain="false" @click="startGame()">スタート</el-button>
    <el-input placeholder="IDを入力してください" v-model="input1" id="ID"></el-input>
    <el-input placeholder="パスワードを入力してください" v-model="input2" show-password id="pass"></el-input>
    <el-button :plain="false" @click="check(input1, input2)">OK</el-button>
    <!-- <el-button :plain="true" @click="success">success</el-button>
    <el-button :plain="true" @click="warning">warning</el-button>
    <el-button :plain="true" @click="error">error</el-button> -->
  </div>
</template>
<script>
import { Message } from 'element-ui';
export default {
  data() {
    return {
      input1: '',
      input2: ''
    }
  },
  method: {
    success() {
      this.$message({
        message: 'アクセスに成功しました。',
        type: 'success'
      });
    },
    warning() {
      this.$message({
        message: 'IDまたはパスワードが間違っています',
        type: 'warning'
      });
    },
    error() {
      this.$message.error('パスワードを3回以上間違えたためアクセスできません。');
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
var input_ID = Message.input1;
var input_pass = Message.input2;
function startGame() {
  for (let i = 0; i < 30; i++) {
    password.push(getRandomInt(0, 20));
    limitcount.push(0);
  }
}
function check(input_ID, input_pass) {
  input_ID = parseInt(input_ID, 10);
  input_pass = parseInt(input_pass, 10);
  if(limitcount[index] >= 3) {
    Message.error();
    console.log(error);
  } else {
    if(password[input_ID] == input_pass) {
      Message.success();
      limitcount[input_ID] = 0;
      console.log(success);
    } else {
      limitcount[input_ID] = limitcount[input_ID] + 1;
      Message.warning();
      console.log(warning);
    }
  }
}
// 繰り返し処理の開始
function startShowing() {
  PassageID = setInterval('showPassage()',1000);
}
// 繰り返し処理の中止
function stopShowing() {
  clearInterval( PassageID );
}
// 繰り返し処理の中身
function showPassage() {
  //  ～ 何らかの処理 ～

}
</script>