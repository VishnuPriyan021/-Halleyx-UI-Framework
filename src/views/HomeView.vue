<template>
<div class="body">

<img src="~@/assets/img/logo.png" alt="">
<h1 class="title">Halleyx UI kit</h1>
<p><b>Halleyx UI kit </b> a collection of UI elements and assets, curated to serve for every designer's and developer's need.</p>
</div>

</template>
<style lang="scss" scoped>
@import '../assets/styles/common/var.scss';

.body{
    /* margin-top: 50px; */
    display: flex;
    height: 100%;
    width: 100%;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    img{
      // margin-left: -90px;
    }
    h1{
      // margin-left: -90px;
      margin-bottom: 30px;
      font-family: QuickSand;
    }
    p{
      text-align: center;
    }
}
</style>

<script>
import { ref } from 'vue'

export default {
  name: 'HomeView',
  components: {
  },
  data () {
    return {
      value: ref(''),
      options: [
        {
          value: 'HTML',
          label: 'HTML'
        },
        {
          value: 'CSS',
          label: 'CSS'
        },
        {
          value: 'JavaScript',
          label: 'JavaScript'
        }
      ]
    }
  }
}
</script>
