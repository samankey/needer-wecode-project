<template>
  <div class="workIndicator">
    <div class="workSummary">
      <div class="totalWorkHour">
        <div class="totalWorkHourStatus">
          <p class="totalWork">총 예정 근무</p>
          <WorkStatus v-if="status < 30">소정 근무 시간 미달</WorkStatus>
          <WorkStatus v-else-if="status > 52" color="#F14425">
            소정 근무 시간 초과
          </WorkStatus>
          <WorkStatus v-else color="#26D434">GOOD</WorkStatus>
        </div>
        <div class="workHour">
          <p class="hour">16.89</p>
          <p class="hourText">시간</p>
        </div>
      </div>
      <div class="workDetails">
        <p class="detailInfo">근무 상세</p>
        <div class="details">
          <div class="info">
            <img
              src="https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/120/apple/285/woman-technologist_1f469-200d-1f4bb.png"
              alt="fire"
            />
            <p>13</p>
          </div>
          <div class="info">
            <img
              src="https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/120/apple/285/fire_1f525.png"
              alt="fire"
            />
            <p>2.3</p>
          </div>
        </div>
      </div>
    </div>
    <div class="workProgressBar"></div>
  </div>
</template>

<script>
import WorkStatus from '../../components/WorkStatus.vue'

export default {
  components: {
    WorkStatus,
  },

  data() {
    return {
      status: 40,
    }
  },
}
</script>

<style lang="scss" scoped>
.workIndicator {
  max-width: 66.6667%;
  flex-basis: 66.6667%;

  .workSummary {
    display: flex;

    .totalWorkHour {
      .totalWorkHourStatus {
        display: flex;
        align-items: center;
        padding-bottom: 22px;
        width: 185px;
        color: rgb(139, 152, 167);

        .totalWork {
          padding: 3px 6px 0 0;
        }
      }
      .workHour {
        display: flex;
        align-items: center;
        color: rgb(139, 152, 167);
        font-size: 40px;
        font-weight: 700;

        .hourText {
          padding-left: 8px;
          font-size: 14px;
          font-weight: 400;
        }
      }
    }

    .workDetails {
      margin-left: 110px;

      .detailInfo {
        margin-bottom: 30px;
        padding: 3px 6px 0 0;
        color: rgb(139, 152, 167);
      }
      .details {
        display: flex;

        .info {
          display: flex;
          align-items: flex-end;
          font-size: 24px;
          font-weight: 600;

          img {
            width: 28px;
          }

          p {
            padding-left: 15px;
          }
        }

        div {
          margin-right: 40px;
        }
      }
    }
  }

  .workProgressBar {
    margin: 35px 0 30px;
    width: calc(100% - 8px);
    height: 14px;
    border-radius: 999px;
    background-color: rgb(236, 236, 236);
  }
}
</style>
