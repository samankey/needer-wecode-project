<template>
  <div>
    <div class="handler">
      <div v-if="isMonthly === true" class="dateHandler">
        <button class="arrowHandler" @click="handleMonth('prev')">
          <font-awesome-icon :icon="['fa', 'chevron-left']" />
        </button>
        <p class="dateIndicator">{{ year }}년 {{ month }}월</p>
        <button class="arrowHandler" @click="handleMonth('next')">
          <font-awesome-icon :icon="['fa', 'chevron-right']" />
        </button>
      </div>
      <div v-else class="dateHandler">
        <button class="arrowHandler" @click="handleWeek('prev')">
          <font-awesome-icon :icon="['fa', 'chevron-left']" />
        </button>
        <p class="dateIndicator">{{ weekly[0] }} - {{ weekly[6] }}</p>
        <button class="arrowHandler" @click="handleWeek('next')">
          <font-awesome-icon :icon="['fa', 'chevron-right']" />
        </button>
      </div>
      <button @click="backToday()">오늘</button>
      <button @click="handleMonthlyBtn()">월</button>
      <button @click="handleWeeklyBtn()">주</button>
    </div>
    <div v-if="isMonthly === true" class="daysContainer">
      <div class="categoryWrap">
        <div class="scCategory">날짜 구성원</div>
      </div>
      <div class="daysWrap">
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
export default {
  data() {
    return {
      year: 0,
      month: 0,
      prevLastDate: 0,
      thisLastDate: 0,
      PLDate: 0,
      PLDay: 0,
      TLDate: 0,
      TLDay: 0,
      dates: [],
      weekly: [],
      date: new Date(),
      today: new Date().getDate(),
      dayOfWeek: new Date().getDay(),
      thisMonth: new Date().getMonth() + 1,
      thisYear: new Date().getFullYear(),
      isMonthly: true,
      dateArray: [],
    }
  },

  computed: {},

  created() {
    this.init()
    this.weeklySchedule()
  },

  methods: {
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
      this.today = this.date.getDate()

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

      const nn = this.weekly[0].split('.')[1]
      const kk = this.weekly[6].split('.')[1]

      if (nn > kk) {
        this.thisMonth = this.date.getMonth() + 1
      }

      return this.weekly
    },

    handleWeek(p) {
      if (p === 'prev') {
        this.today = this.date.setDate(this.today - 7)
        this.weeklySchedule()
      } else {
        this.today = this.date.setDate(this.today + 7)
        this.weeklySchedule()
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
  display: flex;
  align-items: center;
  box-shadow: rgba(20, 20, 20, 0.02) 2px 8px 12px 0px,
    rgba(20, 20, 20, 0.02) 0px 1px 3px 0px;

  .daysWrap {
    display: flex;

    .dates {
      display: flex;
      align-items: center;
      height: 72px;
      padding: 20px;
      border-right: 1px solid rgb(231, 231, 231);
      border-top: 1px solid rgb(231, 231, 231);
      border-bottom: 1px solid rgb(231, 231, 231);
    }

    .today {
      color: #fff;
      background-color: rgb(37, 66, 233);
    }
  }

  .categoryWrap {
    display: flex;
    width: 190px;
    height: 72px;

    .scCategory {
      width: 190px;
      height: 72px;
      border: 1px solid rgb(231, 231, 231);
      padding: 10px 10px 10px 20px;
      display: flex;
      align-items: center;
      font-weight: 500;
    }
  }
}
</style>
