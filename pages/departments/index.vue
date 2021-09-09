<template>
  <div>
    <div class="handler">
      <div class="dateHandler">
        <button class="arrowHandler" @click="handleArrow('prev')">
          <font-awesome-icon :icon="['fa', 'chevron-left']" />
        </button>
        <p class="dateIndicator">{{ handleNav() }}</p>
        <button class="arrowHandler" @click="handleArrow('next')">
          <font-awesome-icon :icon="['fa', 'chevron-right']" />
        </button>
      </div>
      <button @click="backToday()">오늘</button>
      <button @click="handleMonthlyBtn()">월</button>
      <button @click="handleWeeklyBtn()">주</button>
      <div>
        <button class="workType" @click="toggleOnOff()">근무 확인</button>
        <Check v-if="workTypeButton" />
      </div>
      <div class="modalWrap">
        <Modalview v-if="isModalViewed" @close-modal="modalSearch()">
          <Modal />
        </Modalview>
        <button
          class="modalButton"
          @click="
            isModalViewed = true
            modalSearchQuery()
          "
        >
          내 스케줄
        </button>
      </div>
    </div>
    <div v-if="isMonthly === true" class="daysContainer">
      <div class="daysWrap">
        <div class="category">
          <div class="scCategory">날짜 구성원</div>
        </div>
        <div
          v-for="(d, index) in dates"
          :key="index"
          :class="
            today === d && thisMonth === month && thisYear === year
              ? 'dates today'
              : 'dates'
          "
        >
          {{ d }}
        </div>
      </div>
    </div>
    <div v-else class="daysContainer">
      <div class="categoryWrap">
        <div class="scCategory">날짜 구성원</div>
      </div>
      <div class="daysWrap">
        <div
          v-for="(d, index) in weekly"
          :key="index"
          :class="
            today === d && thisMonth === month && thisYear === year
              ? 'dates today'
              : 'dates'
          "
        >
          {{ d }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Modal from './components/Modal'
import Modalview from './components/Modalview'
import Check from './components/Check.vue'

export default {
  components: {
    Modal,
    Modalview,
    Check,
  },

  data() {
    return {
      year: 0, // 월 단위에서 쓰임, 바뀌는 값
      month: 0, // 바뀌는 값, month 값을 사용하는 곳에서
      thisLastDate: 0, // year, month가 변경되면 바뀌는 해당 달 마지막 날 구하는 값
      TLDate: 0, // thisLastDate의 날짜 값
      dates: [], // 월 단위 날짜 데이터
      weekly: [], // 주 단위 날짜 데이터
      date: new Date(), // 오늘 기준의 Date 추출
      today: new Date().getDate(), // 오늘 기준 날짜 추출
      dayOfWeek: new Date().getDay(), // 오늘 기준 요일 추출
      thisMonth: new Date().getMonth() + 1, // 오늘 기준 달 추출
      thisYear: new Date().getFullYear(), // 오늘 기준 년도 추출
      isMonthly: true, // 월/주 변경 boolean
      isModalViewed: false, // 모달 버튼
      workTypeButton: false,
    }
  },

  computed: {},

  created() {
    this.init()
    this.weeklySchedule()
  },
  // 모달서치 함수 삼항연산자 고려해보기 변수명 다시 짓기
  methods: {
    modalSearch() {
      this.$router.push({ path: 'departments' })
      return (this.isModalViewed = false)
    },

    modalSearchQuery() {
      if (this.isModalViewed === true) {
        this.$router.push({ path: 'departments', query: { plan: 'private' } })
      }
    },

    toggleOnOff() {
      this.workTypeButton = !this.workTypeButton
    },

    getLastDate() {
      this.thisLastDate = new Date(this.year, this.month, 0)
      this.TLDate = this.thisLastDate.getDate()
    },

    init() {
      this.year = this.date.getFullYear()
      this.month = this.date.getMonth() + 1

      this.getLastDate()

      this.dates = [...Array(this.TLDate + 1).keys()].slice(1)
    },

    handleMonth(p) {
      if (p === 'prev') {
        this.month = this.date.setMonth(this.date.getMonth() - 1)
        this.init()
      } else {
        this.month = this.date.setMonth(this.date.getMonth() + 1)
        this.init()
      }
    },

    weeklySchedule() {
      for (let i = 0; i < 7; i++) {
        const resultDay = new Date(
          this.thisYear,
          this.thisMonth - 1,
          this.today + (i - this.dayOfWeek)
        )

        const mm = resultDay.getMonth()
        const dd = resultDay.getDate()

        this.weekly[i] = mm + 1 + '.' + dd
      }
      return this.weekly
    },

    handleWeek(p) {
      if (p === 'prev') {
        this.today = this.today - 7
        this.weeklySchedule()
      } else {
        this.today = this.today + 7
        this.weeklySchedule()
      }
    },

    handleNav() {
      if (this.isMonthly) {
        return this.year + '년 ' + this.month + '월'
      } else {
        return this.weekly[0] + ' - ' + this.weekly[6]
      }
    },

    handleArrow(p) {
      if (this.isMonthly) {
        this.handleMonth(p)
      } else {
        this.handleWeek(p)
      }
    },

    backToday() {
      this.date = new Date()
      this.init()
    },

    handleWeeklyBtn() {
      this.isMonthly = false
    },

    handleMonthlyBtn() {
      this.isMonthly = true
    },
  },
}
</script>

<style lang="scss" scoped>
.handler {
  display: flex;
  justify-content: center;
  align-items: center;

  .dateHandler {
    display: flex;
    justify-content: center;
    align-items: center;

    .arrowHandler {
      background: none;
      border: none;
      cursor: pointer;
    }

    .dateIndicator {
      margin: 20px 0;
      padding: 0 20px;
    }
  }
}

.daysContainer {
  min-width: 1120px;

  .daysWrap {
    display: flex;
    height: 72px;

    .category {
      display: flex;
      align-items: center;
      height: 100%;
      position: sticky;
      left: 0;
      border: 1px solid;

      .scCategory {
        width: 190px;
        padding: 0 20px;
      }
    }

    .dates {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 100%;
      height: 100%;
      border-top: 1px solid #111;
      border-bottom: 1px solid #111;
      border-right: 1px solid #111;
    }

    .today {
      color: #fff;
      background-color: rgb(37, 66, 233);
    }
  }
}

.modalButton {
}

.workType {
  position: relative;
}
</style>
