<template>
  <div>
    <i-navbar variant="light">
      <i-navbar-brand :to="{ name: 'Home' }">Page Title</i-navbar-brand>
      <i-navbar-items>
        <i-nav>
          <i-nav-item v-for="page in pages" :key="page.route" :to="{ name: page.route }">{{page.title}}</i-nav-item>
        </i-nav>
      </i-navbar-items>
    </i-navbar>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name:'App',
  data() {
    return {
      pages:[
        {title:'Home', route:'Home'},
        {title:'Music', route:'About'},
      ]
    }
  }
}
</script>

<style>
</style>
