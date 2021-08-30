<template>
  <div class="nowWrapper">
    <div class="summaryWrapper">
      <div class="summary">
        <WorkIndicators />
        <div class="empty"></div>
        <WorkOffSummary />
      </div>
      <div class="workHourRecord">
        <div class="dot"></div>
        <p>자동 근무 기록</p>
        <p>오전 09:30 ~ 오후 06:30</p>
      </div>
    </div>
    <UserInfoSummary />
  </div>
</template>

<script>
import WorkIndicators from './WorkIndicators.vue'
import WorkOffSummary from './WorkOffSummary.vue'
import UserInfoSummary from './UserInfoSummary.vue'

export default {
  components: {
    WorkIndicators,
    WorkOffSummary,
    UserInfoSummary,
  },
  data() {
    return {
      resultData: [{}, {}],
    }
  },
}
</script>

<style lang="scss" scoped>
.nowWrapper {
  min-width: 960px;
  max-width: 1200px;
  padding: 0px 36px;
  box-sizing: border-box;
  font-size: 14px;

  .summaryWrapper {
    padding: 40px 44px 32px 36px;
    background: #fff;
    border-radius: 12px;
    box-shadow: rgba(20, 20, 20, 0.02) 2px 8px 12px 0px,
      rgba(20, 20, 20, 0.02) 0px 1px 3px 0px;

    .summary {
      display: flex;
      justify-content: flex-start;
      width: 100%;
      box-sizing: border-box;
    }

    .empty {
      max-width: 8.33333%;
      flex-basis: 8.33333%;
    }

    .workHourRecord {
      display: flex;
      align-items: center;

      .dot {
        margin-right: 10px;
        width: 10px;
        height: 10px;
        border-radius: 999px;
        background-color: rgb(83, 196, 139);
      }

      p:first-of-type {
        margin-right: 20px;
        color: rgb(99, 114, 131);
      }

      p:last-of-type {
        font-weight: 600;
      }
    }
  }
}
</style>
