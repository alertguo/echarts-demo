<template>
  <div ref="container">
  </div>
</template>

<script>
import echarts from 'echarts'

export default {
  props: ['option', 'loading'],
  mounted() {
    console.log(this.$refs.container)
    const width = document.documentElement.clientWidth
    this.$refs.container.style.width = `${width - 20}px`
    this.$refs.container.style.height = `${width * 1.2 - 20}px`
    this.chart = echarts.init(this.$refs.container, 'dark')
    this.chart.setOption(this.option)
  },
  watch: {
    option() {
      this.chart.setOption(this.option)
    },
    loading() {
      if (this.loading) {
        this.chart.showLoading()
      } else {
        this.chart.hideLoading()
      }
    }
  }
}
</script>
