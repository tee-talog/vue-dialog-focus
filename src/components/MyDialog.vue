<template>
  <div class="my-dialog-wrapper" @click.prevent="handleClose">
	  <div class="dialog-container" role="dialog" tabindex="-1" ref="dialog">
		  <div class="dialog-header">
			  <slot name="header"></slot>
		  </div>
		  <div class="dialog-body">
			  <slot name="body"></slot>
		  </div>
		  <div class="dialog-footer">
			  <div class="dialog-button" tabindex="0" role="button" @click="handleOk">OK</div>
		  </div>
	  </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue, Emit } from 'vue-property-decorator'

@Component
export default class App extends Vue {
	private beforeFocusElement: Element | null = null

	mounted() {
		this.beforeFocusElement = document.activeElement
		if (this.$refs.dialog instanceof HTMLElement) {
			this.$refs.dialog.focus()
		}
	}

	handleClose() {
		this.close()
	}
	@Emit()
	close() {
		return this.beforeFocusElement
	}

	handleOk() {
		this.ok()
	}
	@Emit()
	ok() {
		return this.beforeFocusElement
	}
}
</script>

<style lang="stylus" scoped>
.my-dialog-wrapper
	height 100vh
	width 100vw
	position fixed
	top 0
	left 0
	display flex
	justify-content center
	align-items center
	z-index 999
	background-color #000000aa

.dialog-container
	min-width 400px
	min-height 200px
	background-color #fff
	display flex
	flex-direction column
	justify-content space-between

.dialog-header
	background-color #ddd
	padding 10px

.dialog-body
	padding 5px

.dialog-footer
	background-color #ddd

.dialog-button
	margin 10px
	padding 5px
	border solid 1px #f88
	background-color #faa
	user-select none
</style>
