<!-- <script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Dialog from './components/Dialog.vue'
</script>

<template>
  <img alt="Vue logo" src="https://cdnfile.corp.kuaishou.com/kc/files/a/knode/manual-upload/logo.png" />
  <p>一个 Vue 3 组件例子</p>
  <Dialog
    title="静夜思"
    :msgs="[
        '床前明月光，疑是地上霜。',
        '举头望明月，低头思故乡。',
    ]" />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style> -->

<script>
export default {
  data() {
    return {
      arr: ['逃脱','迸发', '拾取', '破甲', '魂法','驻足'],
      last_pos : 0
    }
  },
   methods: {
    handleClick(event) {
      let tmp = this.arr[5]
      let r = Math.floor(Math.random()*5)
      this.arr[5] = this.arr[r]
      this.arr[r] = tmp
      this.last_post = r
    }
  }
}
</script>

<template>
   <div>
    <table border="1" width="300" height="100">
      <tr>
        <td>{{arr[0]}}</td>
        <td>{{arr[1]}}</td>
        <td>{{arr[2]}}</td>
        <td>{{arr[3]}}</td>
      </tr>
      <tr>
        <td>{{arr[4]}}</td>
      </tr>
    </table>
     
     <h1>
       【{{arr[last_post]}}】打中了【{{last_post+1}}】,下一本打【{{arr[5]}}】
     </h1>
     
    <button @click="handleClick">
    <slot>
      <h2>
        点我打技能
      </h2>
    </slot>
</button>

  </div>
</template>