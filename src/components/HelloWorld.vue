<template>
  <div class="hello">
    <img @click="onClick" alt="Vue logo" src="../assets/logo.png">

    <h3 >왼발에 맞춰 <span style="color: red">로고</span>를 터치하세요</h3>
    <h3>데이터가 많을수록 정확합니다.</h3>
    <h3>{{ result }}</h3>
    <h3 @click="onInit">초기화</h3>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      result: 0,
      start: null,
      last: null,
      count: 0,
    }
  },
  methods: {
    onClick(){
      console.log('onClick')

      if(this.start == null){
        this.start = new Date().getTime();
        return;
      } 

      this.count++;

      this.last = new Date().getTime();

      const diff = this.last - this.start;
      // console.log('this.last - this.start>', diff)
      // console.log('this.count ', this.count)

      this.result = Math.floor(this.count * 1000 * 60 * 2 / diff)
    },
    onInit(){
      console.log('onInit')

      this.start = null;
      this.last = null;
      this.count = 0;
      this.result = 0;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
