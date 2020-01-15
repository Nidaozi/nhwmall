<template>
  <div id="home">
    <nav-bar class="home-navbar">
      <div slot="center">购物街</div>
    </nav-bar>
  </div>
</template>

<script>
import NavBar from 'components/common/navbar/NavBar'
import { getHomeMultidata } from 'network/home'
export default {
  name: 'Home',
  components: {
    NavBar
  },
  data() {
    return {
      banners: [],
      recommends: []
    }
  },
  created() {
    getHomeMultidata()
      .then(result => {
        console.log(result)

        this.banners = result.data.banner.list
        this.recommends = result.data.recommend.list
      })
      .catch(err => {
        console.log(err)
      })
  }
}
</script>

<style>
.home-navbar {
  background-color: var(--color-tint);
  color: #fff;
}
</style>
