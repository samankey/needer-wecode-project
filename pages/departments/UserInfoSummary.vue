<template>
  <div class="overtimeWrapper">
    <div class="scheduledWrapper">
      <p class="title">예정 연장근무</p>
      <div class="scheduled">
        <div v-if="1 !== 0" class="noScheduled">
          <EmptyList>
            <template #image>
              <img :src="scheduledIcon" alt="scheduledIcon" />
            </template>
            <template #desc>
              <p>예정된 연장근무가 없습니다</p>
            </template>
          </EmptyList>
        </div>
        <div v-else class="scheduledList">
          <p>연장근무 리스트</p>
        </div>
      </div>
    </div>
    <div class="historyWrapper">
      <p class="title">지난 연장근무</p>
      <div class="history">
        <div v-if="1 !== 0" class="noHistory">
          <EmptyList>
            <template #image>
              <img :src="historyIcon" alt="historyIcon" />
            </template>
            <template #desc>
              <p>지난 연장근무가 없습니다</p>
            </template>
          </EmptyList>
        </div>
        <div v-else class="historyList">
          <List />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import EmptyList from '../../components/EmptyList.vue'
import List from '../../components/List.vue'

export default {
  components: {
    EmptyList,
    List,
  },

  data() {
    return {
      scheduledIcon:
        'https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/160/apple/285/person-running_light-skin-tone_1f3c3-1f3fb_1f3fb.png',

      historyIcon:
        'https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/160/apple/285/file-folder_1f4c1.png',
    }
  },
}
</script>

<style lang="scss" scoped>
.overtimeWrapper {
  padding-bottom: 100px;
  min-width: 960px;
  max-width: 1200px;
  color: #111;

  .scheduledWrapper {
    .title {
      padding-bottom: 20px;
      font-size: 20px;
      font-weight: 700;
    }

    .scheduled {
      .noScheduled {
      }
    }
  }

  .historyWrapper {
    .title {
      padding: 40px 0 20px 0;
      font-size: 20px;
      font-weight: 700;
    }

    .history {
      .noHistory {
      }
    }
  }
}
</style>
