<template>
  <ListsPage/>
</template>

<script>
import ListsPage from './components/ListsPage.vue'

export default {
  name: 'App',
  components: {
      ListsPage
  }
}
</script>

<style>
*{
    font-family: Avenir, Helvetica, Arial, sans-serif;
    padding: 0;
    margin: 0;
}
*,
*::before,
*::after {
    box-sizing: border-box;
}
</style>
