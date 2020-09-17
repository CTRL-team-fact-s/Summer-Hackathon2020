<template>
  <div>
    <h2>fakeLogin</h2>
    <el-button :plain="true" @click="start" class="input">スタート</el-button>
    <el-input placeholder="IDを入力" v-model="input1" id="ID" type="number" :disabled=inputdisable class="input"></el-input>
    <el-input placeholder="パスワードを入力" v-model="input2" show-password id="pass" type="number" :disabled=inputdisable class="input"></el-input>
    <el-button :plain="true" @click="finish" class="input">OK</el-button>
    <!-- <el-button :plain="true" @click="success">success</el-button>
    <el-button :plain="true" @click="warning">warning</el-button>
    <el-button :plain="true" @click="error">error</el-button> -->
      
    <div class="time">
      制限時間：  {{ formatTime }}
    </div>
    <div>
      始めるにはスタートボタンを押してください。アクセスに成功するとカウントダウンが止まります。
    </div>
  </div>
</template>
<script>
import { Message } from 'element-ui';
let password;
let limitcount;
var input_ID = Message.input1;
var input_pass = Message.input2;
const time_limit_min = 1;
const time_limit_sec = 30;
export default {
  name: 'timer',
  data() {
    password : [];
    limitcount : [];
    return {
      input1: '',
      input2: '',
      min: time_limit_min,
      sec: time_limit_sec,
      timerOn: false,
      timerObj: null,
      inputdisable: false,
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
      for (let i = 0; i < 98; i++) {
        this.password.push(getRandomInt(0, 20));
        this.limitcount.push(0);
      }
      this.$message('IDとパスワードを入力してください');

      // タイマー処理
      let self = this;
      this.timerObj = setInterval(function() {self.count()}, 1000);
      this.timerOn = true; //timerがOFFであることを状態として保持
      this.inputdisable = false;
      this.min = time_limit_min;
      this.sec = time_limit_sec;
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

          // タイマー処理
          clearInterval(this.timerObj);
          this.timerOn = false; //timerがOFFであることを状態として保持
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
    count: function() {
      if (this.sec <= 0 && this.min >= 1) {
        this.min --;
        this.sec = 59;
      } else if(this.sec <= 0 && this.min <= 0) {
        this.complete();
      } else {
        this.sec --;
      }
    },
    complete: function() {
      if(this.timerOn == true) {
        this.$message.error('制限時間を過ぎたため、アクセスできません。');
      }
      this.inputdisable = true;
      clearInterval(this.timerObj);
      this.timerOn = false; //timerがOFFであることを状態として保持
    }
  },
  computed: {
    formatTime: function() {
      let timeStrings = [
        this.min.toString(),
        this.sec.toString()
      ].map(function(str) {
        if (str.length < 2) {
          return "0" + str;
        } else {
          return str;
        }
      });
      return timeStrings[0] + ":" + timeStrings[1];
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

</script>
<style>
.input {
  margin-top:5px;
  margin-bottom: 5px;
}
.time {
  font-size: 18px;
}
</style>