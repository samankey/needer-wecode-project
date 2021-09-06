<template>
  <div class="scheduleList">
    <div class="scheduleNav">
      <button>고정 출퇴근</button>
      <button>반복 일정 등록</button>
    </div>
    <div class="scheduleDesc">
      <p>이번 주 근무</p>
    </div>
    <div class="scheduleTable">
      <div class="scheduleTableData">
        <div class="date">
          <div>8.23 (월)</div>
        </div>
        <div class="scheduleType">
          <img
            src="https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/120/apple/285/technologist-light-skin-tone_1f9d1-1f3fb-200d-1f4bb.png"
            alt="man"
          />
          <div class="scheduleLabel">
            <p>근무</p>
          </div>
          <div class="hour">오전 09:30 ~ 오후 06:30</div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.scheduleList {
  margin: 20px 0 100px 0;
  background: #fff;
  border-radius: 12px;
  box-shadow: rgba(20, 20, 20, 0.02) 2px 8px 12px 0px,
    rgba(20, 20, 20, 0.02) 0px 1px 3px 0px;

  .scheduleNav {
    display: flex;
    justify-content: space-between;
    padding: 14px 24px 14px 10px;
    border-bottom: 1px solid rgba(190, 190, 190, 0.1);

    button:first-child {
      padding: 0 16px;
      height: 38px;
      border: none;
      border-radius: 10px;
      background-color: #fff;
      font-weight: 500;

      &:hover {
        background-color: rgb(243, 243, 243);
      }
    }

    button:last-child {
      padding: 0 16px;
      height: 38px;
      border: 1px solid rgb(190, 190, 190);
      border-radius: 10px;
      background-color: #fff;
      font-weight: 500;
      box-shadow: rgba(20, 20, 20, 0.02) 2px 8px 12px 0px,
        rgba(20, 20, 20, 0.02) 0px 1px 3px 0px;

      &:hover {
        background-color: rgb(243, 243, 243);
      }
    }
  }

  .scheduleDesc {
    padding: 13px 24px;
    border-bottom: 1px solid rgba(190, 190, 190, 0.1);
    color: rgb(99, 114, 131);
  }

  .scheduleTable {
    padding: 8px 24px;

    .scheduleTableData {
      display: flex;
      align-items: center;

      .date {
        display: flex;
        align-items: center;
        width: 250px;
        min-height: 48px;
        border-right: 1px solid rgba(190, 190, 190, 0.1);

        font: {
          size: 16px;
          weight: 500;
        }
      }

      .scheduleType {
        display: flex;
        align-items: center;
        margin-left: 24px;
        padding: 4px 8px;

        img {
          width: 24px;
        }

        .scheduleLabel {
          margin: 0 14px;
          padding: 0 6px;
          min-width: 16px;
          border-radius: 6px;
          border: 1px solid rgb(219, 219, 219);
          background-color: #fff;

          p {
            height: 20px;
            color: rgb(99, 114, 131);
            font-size: 12px;
            line-height: 21px;
          }
        }
        .hour {
          border-bottom: 1px solid rgba(99, 114, 131, 0.1);
          font-size: 15px;
        }
      }
    }
  }
}
</style>
