<template>
  <div>
    <div
      v-for="({ userName, working }, index) in newItems"
      :key="index"
      class="daysContainer"
    >
      <div class="daysWrap">
        <div class="category">
          <div class="scCategory">
            {{ userName }}
          </div>
        </div>
        <div v-for="({ d }, i) in datesArray" :key="d" class="dateWrapper">
          <div v-if="working[i].gapTime.length > 1" class="tooltip">
            <div class="isWork" @click="isModalViewed = true">근무</div>
            <div class="tooltipText tooltipTop">
              {{ working[i].gapTime }}
            </div>
          </div>
          <ScheduleModal
            v-if="isModalViewed"
            @close-modal="isModalViewed = false"
          >
            <ScheduleInfo />
          </ScheduleModal>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ScheduleModal from './ScheduleModal.vue'
import ScheduleInfo from './ScheduleInfo.vue'

export default {
  components: {
    ScheduleModal,
    ScheduleInfo,
  },

  props: {
    dates: { type: Array, default: null },
    listItemData: { type: Array, default: null },
  },

  data() {
    return {
      datesArray: this.dates,
      listItem: this.listItemData,
      isModalViewed: false,
    }
  },

  computed: {
    newItems() {
      return this.listItem.map((user) => {
        const result = {
          userName: user.user,
        }
        result.working = user.data.map((data) => {
          const startTime = new Date(
            data.date + ' ' + data.setTime.startTime
          ).getTime()

          const endTime = new Date(
            data.date + ' ' + data.setTime.endTime
          ).getTime()

          const minuets = (endTime - startTime) / 1000 / 60

          const gapHours =
            parseInt(minuets / 60) === 0 ? '' : parseInt(minuets / 60) + '시간'

          const gapMinuet = minuets % 60 === 0 ? '' : +(minuets % 60) + '분'
          const gapTime = gapHours + ' ' + gapMinuet

          return {
            companyName: data.companyName,
            dateId: data.id,
            gapTime,
          }
        })
        return result
      })
    },
  },

  created() {},

  methods: {},
}
</script>

<style lang="scss" scoped>
.daysContainer {
  min-width: 1120px;
  box-shadow: rgba(20, 20, 20, 0.02) 2px 8px 12px 0px,
    rgba(20, 20, 20, 0.02) 0px 1px 3px 0px;
  .daysWrap {
    display: flex;
    height: 72px;

    .category {
      display: flex;
      align-items: center;
      height: 100%;
      position: sticky;
      left: 0;
      background-color: #fff;
      border: 1px solid rgb(219, 219, 219);
      border-top: none;

      .scCategory {
        width: 190px;
        padding: 0 20px;
      }
    }

    .dateWrapper {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      width: 100%;
      border: 1px solid rgb(219, 219, 219);
      border-top: none;
      border-left: none;
      background-color: #fff;

      .tooltip {
        display: inline-block;

        .isWork {
          padding: 5px 4px 3px 4px;
          border-radius: 5px;
          background-color: rgb(228, 231, 245);
        }

        .tooltipText {
          display: none;
          position: absolute;
          max-width: 200px;
          border: 1px solid;
          border-radius: 5px;
          margin-top: 8px;
          padding: 5px;
          font-size: 0.8em;
          color: white;
          background: rgb(37, 66, 233);
        }

        &:hover {
          .tooltipText {
            display: block;

            &::after {
              content: ' ';
              position: absolute;
              border-style: solid;
              border-width: 5px;
            }
          }
        }

        .tooltipTop {
          &::after {
            top: -40%;
            left: 10%;
            border-color: transparent transparent rgb(37, 66, 233) transparent;
          }
        }
      }
    }

    /* .today {
      color: #fff;
      background-color: rgb(37, 66, 233);
    } */
  }
}
</style>
