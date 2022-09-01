<template>
  <div>
    <h2>学生姓名：{{ name }}</h2>
    <h2>学生地址：{{ address }}</h2>
    <h2>年龄：{{ age }}</h2>
    <h2 v-if="sex">性别：{{ sex }}</h2>
    <h2 v-if="nickname">小名：{{ nickname }}</h2>
    <h2 v-if="IDCard">身份证：{{ IDCard }}</h2>
  </div>
</template>
<script>
export default {
  name: "Student",
  data() {
    return {
      name: "张三",
      address: "深圳",
      age: 20,
    };
  },
  // props:["sex","nickname","IDCard"]
  // props:{
  //     sex:String,
  //     nickname:String,
  //     IDCard:Number

  // }
  props: {
    sex: {
      type: String,
      required: false,
      default: "女",
    },
    nickname: {
         type: String,
         required: true
    },
    IDCard: {
          type: Number,
         required: true
    },
  },
};
</script>