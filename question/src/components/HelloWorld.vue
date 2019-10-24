<template>
  <div class="hello" v-cloak>
    <div v-if="(count==1)">
      <div class="question">
        <h4>1.请问您的性别是：</h4>
        <label><input type="radio" name="sex" value="男生" v-model="sex">男生</label>
        <label><input type="radio" name="sex" value="女生" v-model="sex">女生</label>
        <label><input type="radio" name="sex" value="保密" v-model="sex">保密</label>
      </div>
      <div class="button">
        <button @click="countAdd()">下一步</button>
        <button @click="sexReset()">重置</button>
      </div>
    </div>
    <div v-if="count==2">
      <div class="question">
        <h4>2.请选择您的兴趣爱好：</h4>
        <label><input type="checkbox" v-model="habbi" name="like" value="看书">看书</label>
        <label><input type="checkbox" v-model="habbi" name="like" value="游泳">游泳</label>
        <label><input type="checkbox" v-model="habbi" name="like" value="跑步">跑步</label>
        <label><input type="checkbox" v-model="habbi" name="like" value="看电影">看电影</label>
        <label><input type="checkbox" v-model="habbi" name="like" value="听音乐">听音乐</label>
      </div>
      <div class="button">
        <button @click="countAdd()" :disabled="hLength()">下一步</button>
        <button @click="countReduce()">上一步</button>
        <button @click="habbiReset()">重置</button>
      </div>
    </div>
    <div v-if="count==3">
      <div class="question">
        <h4>3.请介绍一下自己：</h4>
        <textarea name="txt" v-model="selfIntrodution"></textarea>
      </div>
      <div class="button">
        <button @click="updata()" :disabled="tLength()">提交</button>
        <button @click="countReduce()">上一步</button>
        <button @click="resetPage()">重置</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
        count:1,
        sex:"保密",
        habbi:[],
        selfIntrodution:""
    }
  },
  computed:{

  },
  methods:{
    tLength:function(){
        let length = this.selfIntrodution.split('').length;
        if( length > 5){
            return false
        }else{
          return true
        }
    },
    hLength:function(){
      if( this.habbi.length > 1 && this.habbi.length <4 ){
          return false
      }else{
        return true
      }
    },
    countAdd:function () {
      this.count++;
    },
    countReduce:function () {
      this.count--;
    },
    sexReset:function(){
      this.sex = "保密";
    },
    habbiReset:function () {
      this.habbi = [];
    },
    resetPage:function(){
      this.selfIntrodution = "";
    },
    updata:function () {
      console.log(
        {
          "sex":this.sex,
          "habbi":this.habbi,
          "selfIntrodution":this.selfIntrodution,

        }
      );
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

</style>
