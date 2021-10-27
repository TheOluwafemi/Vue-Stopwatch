<template>
  <div class="home">
    <page-title />
    <timing-indicator />
  </div>
</template>

<script>
  // @ is an alias to /src
  import PageTitle from "@/components/layouts/page-title.vue";
  import TimingIndicator from "@/components/timing/timing-indicator.vue";

  export default {
    name: "Home",
    components: {
      PageTitle,
      TimingIndicator,
    },
  };
</script>

<style lang="scss" scoped>
  .home {
    height: 100vh;
  }
</style>
