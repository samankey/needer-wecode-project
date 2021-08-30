<template>
<<<<<<< HEAD
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
=======
  <div class="department">
    <nav class="handler">
      <div class="dateHandler">
        <button class="arrowHandler" @click="handleArrow('prev')">
          <font-awesome-icon :icon="['fa', 'chevron-left']" />
        </button>
        <p class="dateIndicator">{{ handleNav() }}</p>
        <button class="arrowHandler" @click="handleArrow('next')">
          <font-awesome-icon :icon="['fa', 'chevron-right']" />
        </button>
      </div>
      <div class="buttonWrapper">
        <button class="todayBtn button" @click="backToday()">오늘</button>
        <button class="monthly button" @click="handleMonthlyBtn()">월</button>
        <button class="weekly button" @click="handleWeeklyBtn()">주</button>
      </div>
    </nav>
    <!-- 월단위 -->
    <div v-if="isMonthly === true">
      <div class="daysContainer">
        <div class="daysWrap">
          <div class="category">
            <div class="scCategory">구성원</div>
          </div>
          <div
            v-for="(d, index) in dates"
            :key="index"
            :class="
              today === d && thisMonth === month && thisYear === year
                ? 'dateWrapper today'
                : 'dateWrapper'
            "
          >
            <div class="dates">
              {{ d }}
            </div>
          </div>
        </div>
      </div>
      <ScheduleList :dates="dates" :list-item-data="listItemData" />
    </div>
    <!-- 주단위 -->
    <div v-else>
      <div class="daysContainer">
        <div class="daysWrap">
          <div class="category">
            <div class="scCategory">구성원</div>
          </div>
          <div
            v-for="(d, index) in weekly"
            :key="index"
            :class="
              today.toString() === d.split('.')[1] &&
              thisMonth.toString() === d.split('.')[0] &&
              thisYear === year
                ? 'dateWrapper today'
                : 'dateWrapper'
            "
          >
            <div class="dates">
              {{ d }}
            </div>
            <div>요일</div>
          </div>
>>>>>>> e60caf4 (Add: 레이아웃 추가 및 모달 구현)
        </div>
      </div>
    </div>
  </div>
</template>

<script>
<<<<<<< HEAD
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

=======
import ScheduleList from './ScheduleList.vue'
export default {
  components: {
    ScheduleList,
  },

  data() {
    return {
      listItemData: [
        {
          user: '샘코딩',
          data: [
            {
              id: 1,
              workid: 'samankeyc',
              date: '2021-09-01',
              companyName: '삼촌네',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '',
                endTime: '',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 2,
              workid: 'samankeyc',
              date: '2021-09-02',
              companyName: '삼촌네',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 3,
              workid: 'samankeyc',
              date: '2021-09-03',
              companyName: '삼촌네',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:34',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 4,
              workid: 'samankeyc',
              date: '2021-09-04',
              companyName: '삼촌네',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 5,
              workid: 'samankeyc',
              date: '2021-09-05',
              companyName: '삼촌네',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 6,
              workid: 'samankeyc',
              date: '2021-09-06',
              companyName: '삼촌네',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 7,
              workid: 'samankeyc',
              date: '2021-09-07',
              companyName: '삼촌네',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '',
                endTime: '',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 8,
              workid: 'samankeyc',
              date: '2021-09-08',
              companyName: '삼촌네',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '',
                endTime: '',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 9,
              workid: 'samankeyc',
              date: '2021-09-09',
              companyName: '삼촌네',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 10,
              workid: 'samankeyc',
              date: '2021-09-10',
              companyName: '삼촌네',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '18:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 11,
              workid: 'samankeyc',
              date: '2021-09-01',
              companyName: '싸와디',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:34',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 12,
              workid: 'samankeyc',
              date: '2021-09-01',
              companyName: '싸와디',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 13,
              workid: 'samankeyc',
              date: '2021-09-01',
              companyName: '싸와디',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 14,
              workid: 'samankeyc',
              date: '2021-09-01',
              companyName: '싸와디',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '',
                endTime: '',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 15,
              workid: 'samankeyc',
              date: '2021-09-01',
              companyName: '싸와디',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '',
                endTime: '',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 16,
              workid: 'samankeyc',
              date: '2021-09-16',
              companyName: '싸와디',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:32',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 17,
              workid: 'samankeyc',
              date: '2021-09-17',
              companyName: '싸와디',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:50',
                endTime: '17:14',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 18,
              workid: 'samankeyc',
              date: '2021-09-18',
              companyName: '싸와디',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:53',
                endTime: '17:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 19,
              workid: 'samankeyc',
              date: '2021-09-19',
              companyName: '싸와디',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:59',
                endTime: '17:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 20,
              workid: 'samankeyc',
              date: '2021-09-20',
              companyName: '싸와디',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:27',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 21,
              workid: 'samankeyc',
              date: '2021-09-21',
              companyName: '매머드커피',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '',
                endTime: '',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 22,
              workid: 'samankeyc',
              date: '2021-09-22',
              companyName: '매머드커피',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '',
                endTime: '',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 23,
              workid: 'samankeyc',
              date: '2021-09-23',
              companyName: '매머드커피',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 24,
              workid: 'samankeyc',
              date: '2021-09-24',
              companyName: '매머드커피',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:01',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 25,
              workid: 'samankeyc',
              date: '2021-09-25',
              companyName: '매머드커피',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:04',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 26,
              workid: 'samankeyc',
              date: '2021-09-26',
              companyName: '매머드커피',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:52',
                endTime: '17:29',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 27,
              workid: 'samankeyc',
              date: '2021-09-27',
              companyName: '매머드커피',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:40',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 28,
              workid: 'samankeyc',
              date: '2021-09-28',
              companyName: '매머드커피',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '',
                endTime: '',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 29,
              workid: 'samankeyc',
              date: '2021-09-29',
              companyName: '매머드커피',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '',
                endTime: '',
              },
              isTimeOver: false,
              isToWork: false,
            },
            {
              id: 30,
              workid: 'samankeyc',
              date: '2021-09-30',
              companyName: '매머드커피',
              getTime: {
                startTime: '11:00',
                endTime: '17:00',
              },
              setTime: {
                startTime: '10:55',
                endTime: '17:30',
              },
              isTimeOver: false,
              isToWork: false,
            },
          ],
        },
      ],
      year: 0, // 월 단위에서 쓰임, 바뀌는 값
      month: 0, // 바뀌는 값, month 값을 사용하는 곳에서
      thisLastDate: 0, // year, month가 변경되면 바뀌는 해당 달 마지막 날 구하는 값
      TLDate: 0, // thisLastDate의 날짜 값
      dates: [], // 월 단위 날짜 데이터
      weekly: [], // 주 단위 날짜 데이터
      date: new Date(), // 오늘 기준의 Date 추출
      today: new Date().getDate(), // 오늘 기준 날짜 추출
      thisToday: new Date().getDate(),
      dayOfWeek: new Date().getDay(), // 오늘 기준 요일 추출
      thisMonth: new Date().getMonth() + 1, // 오늘 기준 달 추출
      thisYear: new Date().getFullYear(), // 오늘 기준 년도 추출
      isMonthly: true, // 월/주 변경 boolean
      isModalViewed: false,
    }
  },

  computed: {},

  created() {
    this.init()
    this.weeklySchedule()
  },

  methods: {
>>>>>>> e60caf4 (Add: 레이아웃 추가 및 모달 구현)
    init() {
      this.year = this.date.getFullYear()
      this.month = this.date.getMonth() + 1

<<<<<<< HEAD
      this.getLastDate()
=======
      this.thisLastDate = new Date(this.year, this.month, 0)
      this.TLDate = this.thisLastDate.getDate()
>>>>>>> e60caf4 (Add: 레이아웃 추가 및 모달 구현)

      this.dates = [...Array(this.TLDate + 1).keys()].slice(1)
    },

<<<<<<< HEAD
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
=======
    weeklySchedule() {
      for (let i = 0; i < 7; i++) {
        const resultDay = new Date(
          this.thisYear,
          this.thisMonth - 1,
          this.thisToday + (i - this.dayOfWeek)
        )

        const mm = resultDay.getMonth()
        const dd = resultDay.getDate()

        this.weekly[i] = mm + 1 + '.' + dd
      }

      return this.weekly
    },

    handleMonth(p) {
      if (p === 'prev') {
        this.month = this.date.setMonth(this.date.getMonth() - 1)
        this.init()
      } else {
        this.month = this.date.setMonth(this.date.getMonth() + 1)
        this.init()
      }
>>>>>>> e60caf4 (Add: 레이아웃 추가 및 모달 구현)
    },

    handleWeek(p) {
      if (p === 'prev') {
<<<<<<< HEAD
        this.today = this.date.setDate(this.today - 7)
        this.weeklySchedule()
      } else {
        this.today = this.date.setDate(this.today + 7)
=======
        this.thisToday = this.thisToday - 7
        this.weeklySchedule()
      } else {
        this.thisToday = this.thisToday + 7
>>>>>>> e60caf4 (Add: 레이아웃 추가 및 모달 구현)
        this.weeklySchedule()
      }
    },

<<<<<<< HEAD
=======
    handleNav() {
      if (this.isMonthly) {
        return this.year + '년 ' + this.month + '월'
      } else {
        return this.weekly[0] + ' - ' + this.weekly[6]
      }
    },

>>>>>>> e60caf4 (Add: 레이아웃 추가 및 모달 구현)
    backToday() {
      this.date = new Date()
      this.init()
    },

    handleWeeklyBtn() {
      this.isMonthly = false
    },

    handleMonthlyBtn() {
      this.isMonthly = true
<<<<<<< HEAD
=======
    },

    handleArrow(p) {
      if (this.isMonthly) {
        this.handleMonth(p)
      } else {
        this.handleWeek(p)
      }
>>>>>>> e60caf4 (Add: 레이아웃 추가 및 모달 구현)
    },
  },
}
</script>

<style lang="scss" scoped>
<<<<<<< HEAD
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
=======
.department {
  .handler {
>>>>>>> e60caf4 (Add: 레이아웃 추가 및 모달 구현)
    display: flex;
    justify-content: center;
    align-items: center;
    color: rgb(56, 56, 56);
    background-color: #fff;

<<<<<<< HEAD
    .dates {
=======
    .dateHandler {
>>>>>>> e60caf4 (Add: 레이아웃 추가 및 모달 구현)
      display: flex;
      justify-content: center;
      align-items: center;
<<<<<<< HEAD
      height: 72px;
      padding: 20px;
      border-right: 1px solid rgb(231, 231, 231);
      border-top: 1px solid rgb(231, 231, 231);
      border-bottom: 1px solid rgb(231, 231, 231);
    }

    .today {
      color: #fff;
      background-color: rgb(37, 66, 233);
=======
      padding: 3px 0 0 0;

      .arrowHandler {
        padding: 6px 5px 5px;
        background: none;
        border: none;
        cursor: pointer;

        &:hover {
          border-radius: 5px;
          background-color: rgb(235, 235, 235);
        }
      }

      .dateIndicator {
        margin: 20px 10px;
        padding: 6px 20px 3px 20px;

        &:hover {
          border-radius: 5px;
          background-color: rgb(235, 235, 235);
        }
      }
    }

    .buttonWrapper {
      margin-left: 10px;
      padding: 3px 0 0 0;

      .button {
        padding: 5px 4px;
        width: 50px;
        background-color: #fff;
        border: none;
        font: {
          size: 14px;
          weight: 600;
        }
        color: rgb(56, 56, 56);
        cursor: pointer;

        &:hover {
          border-radius: 5px;
          background-color: rgb(235, 235, 235);
        }
      }

      .todayBtn {
        color: rgb(37, 66, 233);
      }
>>>>>>> e60caf4 (Add: 레이아웃 추가 및 모달 구현)
    }
  }

  .daysContainer {
    min-width: 1120px;
    z-index: 1;

<<<<<<< HEAD
    .scCategory {
      width: 190px;
      height: 72px;
      border: 1px solid rgb(231, 231, 231);
      padding: 10px 10px 10px 20px;
=======
    .daysWrap {
>>>>>>> e60caf4 (Add: 레이아웃 추가 및 모달 구현)
      display: flex;
      height: 72px;
      box-shadow: rgba(20, 20, 20, 0.02) 2px 8px 12px 0px,
        rgba(20, 20, 20, 0.02) 0px 1px 3px 0px;

      .category {
        display: flex;
        align-items: center;
        height: 100%;
        position: sticky;
        left: 0;
        background-color: #fff;
        border: 1px solid rgb(219, 219, 219);

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
        border-left: none;
        background-color: rgb(235, 238, 255);

        .dates {
        }
      }

      .today {
        color: #fff;
        background-color: rgb(37, 66, 233);
      }
    }
  }
}
</style>
