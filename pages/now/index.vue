<template>
  <div class="nowWrapper">
    <div class="summary">
      <div class="workIndicator">
        <div class="workSummary">
          <div class="totalWorkHour">
            <div class="totalWorkHourStatus">
              <p class="totalWork">총 예정 근무</p>
              <p class="status">소정 근로 시간 미달</p>
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
        <div class="workHourRecord">
          <div class="dot"></div>
          <p>자동 근무 기록</p>
          <p>오전 09:30 ~ 오후 06:30</p>
        </div>
      </div>
      <div class="workOffSummary">
        <div class="workOffDesc">
          <p>유급휴가</p>
          <font-awesome-icon :icon="['far', 'question-circle']" />
        </div>
        <div class="workOffDetails">
          <img
            src="https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/120/apple/285/beach-with-umbrella_1f3d6-fe0f.png"
            alt="beach"
          />
          <p>없음</p>
        </div>
        <div class="workOffProgressBar"></div>
      </div>
    </div>
    <div class="scheduleList">안녕</div>
  </div>
</template>

<script>
export default {}
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

    .workIndicator {
      .workSummary {
        display: flex;

        .totalWorkHour {
          .totalWorkHourStatus {
            display: flex;
            align-items: center;
            padding-bottom: 22px;
            color: rgb(139, 152, 167);

            .totalWork {
              padding: 3px 6px 0 0;
            }

            .status {
              padding: 5px 9px 3px 9px;
              border-radius: 999px;
              color: #fff;
              background-color: rgb(139, 152, 167);
              font-size: 12px;
              font-weight: 400;
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
        height: 14px;
        border-radius: 999px;
        background-color: rgb(236, 236, 236);
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

    .workOffSummary {
      margin-left: 80px;

      .workOffDesc {
        display: flex;
        margin-bottom: 30px;
        padding-right: 140px;
        color: rgb(139, 152, 167);

        p {
          padding-right: 10px;
        }
      }

      .workOffDetails {
        display: flex;
        align-items: flex-end;
        font-size: 24px;
        font-weight: 600;

        img {
          width: 28px;
        }

        p {
          padding-left: 15px;
          color: rgba(20, 20, 20, 0.2);
        }
      }

      .workOffProgressBar {
        margin: 45px 0 30px;
        height: 14px;
        border-radius: 999px;
        background-color: rgb(236, 236, 236);
      }
    }
  }

  .scheduleList {
    margin-top: 20px;
    padding: 40px 44px 32px 36px;
    width: 890px;
    background: #fff;
    border-radius: 12px;
    box-shadow: rgba(20, 20, 20, 0.02) 2px 8px 12px 0px,
      rgba(20, 20, 20, 0.02) 0px 1px 3px 0px;
  }
}
</style>
