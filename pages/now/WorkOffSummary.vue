<template>
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
</template>

<style lang="scss" scoped>
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
</style>
