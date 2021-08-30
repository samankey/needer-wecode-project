<template>
  <div class="workSummaryContainer">
    <div class="workSummaryTitle">
      <div class="dot"></div>
      <p>summary</p>
    </div>
    <div class="todayScheduledTime">
      <p>근무 예정 시간</p>
      <p>오전 11 : 00 ~ 오후 17 : 00</p>
    </div>
    <div class="workTimeSummaryWrapper">
      <div class="summary">
        <div class="summaryTitle">일한 시간</div>
        <div>
          <p class="timeTitle">출근</p>
          <p class="startTime">오전 10 : 55</p>
          <p class="timeTitle">퇴근</p>
          <p class="endTime">오후 17 : 05</p>
          <p class="timeTitle">총 근무 시간</p>
          <p class="totalTime">6시간 10분</p>
        </div>
      </div>
      <div class="summary">
        <div class="summaryTitle">초과 근무 시간</div>
        <div class="overtimeWrapper">
          <span class="large">0</span>
          <span class="small">시간</span>
          <span class="large">10</span>
          <span class="small">분</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {},
}
</script>

<style lang="scss" scoped>
.workSummaryContainer {
  color: #111;
  .workSummaryTitle {
    margin-bottom: 30px;
    height: 40px;

    .dot {
      width: 10px;
      height: 10px;
      border-radius: 999px;
      background-color: rgb(37, 66, 233);
    }

    p {
      padding: 5px 0;

      font: {
        size: 30px;
        weight: 600;
      }
    }
  }

  .todayScheduledTime {
    display: flex;
    align-items: center;
    margin-bottom: 30px;
    height: 40px;
    border-radius: 10px;
    background-color: #fff;
    box-shadow: rgba(20, 20, 20, 0.02) 2px 8px 12px 0px,
      rgba(20, 20, 20, 0.02) 0px 1px 3px 0px;

    p {
      padding: 5px 20px;

      &:first-child {
        border-right: 1px solid rgb(219, 219, 219);
        font-weight: 500;
      }
    }
  }

  .workTimeSummaryWrapper {
    display: flex;
    justify-content: space-between;

    .summary {
      padding: 20px 20px;
      width: 50%;
      height: 300px;
      border-radius: 10px;
      background-color: #fff;
      box-shadow: rgba(20, 20, 20, 0.02) 2px 8px 12px 0px,
        rgba(20, 20, 20, 0.02) 0px 1px 3px 0px;

      &:first-child {
        margin-right: 30px;
      }

      .summaryTitle {
        display: inline-block;
        padding-bottom: 5px;
        background-color: rgb(255, 164, 111);
        font-weight: 500;
        line-height: 0.4;

        p {
          text-align: center;
        }
      }

      .timeTitle {
        display: inline-block;
        margin: 20px 0 10px 0;
        padding: 5px;
        border-radius: 5px;
        background-color: rgb(235, 238, 255);
      }

      .overtimeWrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        padding-top: 40px;
        height: 200px;

        .large {
          padding: 10px;
          font: {
            size: 60px;
            weight: 700;
          }
        }

        .small {
          font-size: 20px;
        }
      }
    }
  }
}
</style>
