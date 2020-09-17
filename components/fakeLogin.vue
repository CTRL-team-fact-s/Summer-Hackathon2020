<template>
  <div>
    <h2>fakeLogin</h2>
    <el-button :plain="true" @click="start">スタート</el-button>
    <el-input placeholder="IDを入力" v-model="input1" id="ID" type="number"></el-input>
    <el-input placeholder="パスワードを入力" v-model="input2" show-password id="pass" type="number"></el-input>
    <el-button :plain="true" @click="finish">OK</el-button>
    <!-- <el-button :plain="true" @click="success">success</el-button>
    <el-button :plain="true" @click="warning">warning</el-button>
    <el-button :plain="true" @click="error">error</el-button> -->
  </div>
</template>
<script>
import { Message } from 'element-ui';
let password;
let limitcount;
var input_ID = Message.input1;
var input_pass = Message.input2;
export default {
  data() {
    password : [];
    limitcount : [];
    return {
      input1: '',
      input2: '',
    }
  },
  methods: {
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
    },
    start: function () {
      // startGame();
      this.password = [19,20];
      this.limitcount = [0,0];
      for (let i = 0; i < 28; i++) {
        this.password.push(getRandomInt(0, 20));
        this.limitcount.push(0);
      }
      this.$message('IDとパスワードを入力してください');
    },
    finish: function () {
      // check();
      input_ID = this.input1;
      input_pass = this.input2;
      console.log(input_ID);
      if(this.limitcount[input_ID] >= 3) {
        // this.error();
        this.$message.error('パスワードを3回以上間違えたためアクセスできません。');
        console.log("error");
      } else {
        if(this.password[input_ID] == input_pass) {
          // this.success();
          this.$message({
            message: 'アクセスに成功しました。',
            type: 'success'
          });
          this.limitcount[input_ID] = 0;
          console.log("success");
        } else {
          this.limitcount[input_ID] = this.limitcount[input_ID] + 1;
          // this.warning();
          this.$message({
            message: 'IDまたはパスワードが間違っています',
            type: 'warning'
          });
          console.log("warning");
        }
      }
    },
    greet: function (event) {
      // `this` inside methods points to the Vue instance
      alert('Hello ' + this.name + '!')
      // `event` is the native DOM event
      if (event) {
        alert(event.target.tagName)
      }
    }
  }
};
function getRandomInt(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min)) + min; //The maximum is exclusive and the minimum is inclusive
};

/*
function startGame(){
  password = [19,20];
  limitcount = [0,0];
  for (let i = 0; i < 28; i++) {
    password.push(getRandomInt(0, 20));
    limitcount.push(0);
  }
};

function check(input_ID, input_pass) {
  if(limitcount[input_ID] >= 3) {
    Message.error();
    console.log(error);
  } else {
    if(password[input_ID] === input_pass) {
      Message.success();
      limitcount[input_ID] = 0;
      console.log(success);
    } else {
      limitcount[input_ID] = limitcount[input_ID] + 1;
      Message.warning();
      console.log(warning);
    }
  }
};
*/

// 繰り返し処理の開始
function startShowing() {
  PassageID = setInterval('showPassage()',1000);
};
// 繰り返し処理の中止
function stopShowing() {
  clearInterval( PassageID );
}
// 繰り返し処理の中身
function showPassage() {
  //  ～ 何らかの処理 ～

}
</script>