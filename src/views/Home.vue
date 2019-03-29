<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>

    <button @click="handleClick('back')">返回上一页</button>
    <button @click="handleClick('push')">跳转到parent</button>
     <button @click="handleClick('replace')">替换到parent</button>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  components: {
    HelloWorld
  },
  methods: {
    handleClick (type) {
      //需要用到路由实例
      // 返回上一页
      if(type === 'back') this.$router.back()
      else if (type === 'push'){
        const name = 'raven'
        //使用push 浏览历史加入一个记录，方便回退
        this.$router.push({
          name: 'argu',
          params: {
            name: 'raven'
          }
          //path: `/argu/${name}`
        // name: 'argu',
        // params: {
        //   name: 'raven'
        // }
        // //添加参数
        // query: {
        //   name: 'raven'
        // }
      })
     } else if (type === 'replace'){
       //使用replace 将当前的浏览历史替换为parent页面
        this.$router.replace({
        name: 'parent'
      })
     }
    }   
  }
}
</script>
