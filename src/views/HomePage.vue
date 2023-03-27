<template>
  <div class="home">
    <div class="container">
      <div class="homepage-wrapper">
        <stop-watch-component v-for="num in amount" :key="num"/>
        <add-stop-watch @click="amount++"/>
      </div>
    </div>
  </div>
</template>

<script>
import StopWatchComponent from "@/components/StopWatchComponent.vue";
import AddStopWatch from '@/components/AddStopWatch.vue';
export default {
  name: "HomePage",
  components: { StopWatchComponent, AddStopWatch },
  data () {
    return {
      amount: 1
    }
  }
};
</script>

<style scoped lang="scss">
.homepage {
  &-wrapper {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    row-gap: 45px;
    justify-items: center;

    @include breakpoint(md) {
      grid-template-columns: 1fr 1fr;
    }
    @include breakpoint(sm) {
      grid-template-columns: 1fr;
    }
  }
}
</style>
