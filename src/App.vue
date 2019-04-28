<template>
  <div id="app">
    <button @click="isDialogShown = true">open1</button>
    <button @click="isDialogShown = true">open2</button>
    <button @click="isDialogShown = true">open3</button>
    <button @click="isDialogShown = true">open4</button>
    <button @click="isDialogShown = true">open5</button>
    <button @click="isDialogShown = true">open6</button>
    <button @click="isDialogShown = true">open7</button>
    <button @click="isDialogShown = true">open8</button>
    <button @click="isDialogShown = true">open9</button>

    <my-dialog v-if="isDialogShown" @ok="handleOk" @close="handleClose">
      <template v-slot:header>
        <div>閉じるダイアログ</div>
      </template>
      <template v-slot:body>
        <div>このダイアログを閉じます。</div>
      </template>
    </my-dialog>

  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import MyDialog from './components/MyDialog.vue';

@Component({
  components: {
    MyDialog,
  },
})
export default class App extends Vue {
  public isDialogShown = false

  handleClose(elm: Element | null) {
    this.isDialogShown = false
    if (elm instanceof HTMLElement) {
      elm.focus()
    }
  }

  handleOk(elm: Element | null) {
    this.isDialogShown = false
    if (elm instanceof HTMLElement) {
      elm.focus()
    }
  }
}
</script>

<style lang="stylus">
#app
  font-family 'Avenir', Helvetica, Arial, sans-serif
  -webkit-font-smoothing antialiased
  -moz-osx-font-smoothing grayscale
  text-align center
  color #2c3e50
  margin-top 60px

button
  margin 10px
</style>
