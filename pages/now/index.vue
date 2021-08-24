<template>
  <div class="nowWrapper">
    <div class="summary">
      <WorkIndicators />
      <WorkOffSummary />
    </div>
    <ScheduleList />
  </div>
</template>

<script>
import WorkIndicators from './WorkIndicators.vue'
import WorkOffSummary from './WorkOffSummary.vue'
import ScheduleList from './ScheduleList.vue'

export default {
  components: {
    WorkIndicators,
    WorkOffSummary,
    ScheduleList,
  },
}
</script>

<style lang="scss" scoped>
.nowWrapper {
  display: flex;
  align-items: center;
  flex-direction: column;
  font-size: 14px;

  .summary {
    display: flex;
    padding: 40px 44px 32px 36px;
    width: 890px;
    background: #fff;
    border-radius: 12px;
    box-shadow: rgba(20, 20, 20, 0.02) 2px 8px 12px 0px,
      rgba(20, 20, 20, 0.02) 0px 1px 3px 0px;
  }
}
</style>
