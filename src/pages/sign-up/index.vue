<template>
  <div class="home container">
    <div class="voice__top-bar">
      <div class="voice__time">{{timeDown}}</div>
      <div class="voice__task-step">当前任务进度：{{steps}}</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      steps: "11"
    };
  }
};
</script>

<style scoped lang="scss">
</style>