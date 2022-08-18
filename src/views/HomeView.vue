<template>
  <div class="home">
    <CalcBox />
  </div>
</template>

<script>
// @ is an alias to /src
import CalcBox from '@/components/Containers/CalcBox/CalcBox.vue'

export default {
  name: 'HomeView',
  components: {
    CalcBox
  }
}
</script>
<style lang="scss" scooped>
@import './HomeView.scss'
</style>
