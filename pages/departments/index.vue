<template>
  <div class="daysContainer">
    <div class="categoryWrap">
      <div class="scCategory">날짜 구성원</div>
    </div>
    <div class="daysWrap">
      <div v-for="(pl, index) in inputProps" :key="index" class="daysArray">
        {{ pl }}
      </div>
    </div>
  </div>
</template>

<script>
import dayjs from 'dayjs'

const utc = require('dayjs/plugin/utc')
const timezone = require('dayjs/plugin/timezone')

dayjs.extend(utc)
dayjs.extend(timezone)

const today = dayjs().tz('Asia/Seoul')

const thisYear = today.year()
const thisMonth = today.month()

const firstDateOfMonth = dayjs([thisYear, thisMonth + 1]).tz('Asia/Seoul')
// .add(9, 'hour')
const daysInMonth = today.daysInMonth()
const endDateOfMonth = firstDateOfMonth.add(daysInMonth, 'day')

const getDatesBetweenDates = (startDate, endDate) => {
  let dates = []
  // to avoid modifying the original date
  const theDate = new Date(startDate)
  while (theDate.valueOf() < endDate.valueOf()) {
    dates = [...dates, new Date(theDate)]
    theDate.setDate(theDate.getDate() + 1)
  }
  console.log('suho:', dates)
  dates = [...dates, endDate]

  return dates
}

const dates = getDatesBetweenDates(firstDateOfMonth, endDateOfMonth)

const datesPop = dates.pop()
console.log('엔시발', datesPop)

export default {
  data() {
    return {
      inputs: dates,
    }
  },

  computed: {
    inputProps() {
      return this.inputs.map((input) =>
        input.toString().split('').slice(8, 10).join('')
      )
    },
  },
  // input.toString().split().slice(2, 3)
  // computed: {
  //   inputProps() {
  //     return this.inputs.map((input, index) => ({
  //       id: index,
  //       className: input.class,
  //       type: input.type,
  //       placeholder: input.placeholder,
  //     }))
  //   },
  // },

  methods: {},
}
</script>

<style lang="scss" scoped>
.daysContainer {
  display: flex;
  align-items: center;

  .daysWrap {
    display: flex;

    .daysArray {
      display: flex;
      align-items: center;
      height: 72px;
      padding: 10px;
      border-right: 1px solid;
      border-top: 1px solid;
      border-bottom: 1px solid;
    }
  }

  .categoryWrap {
    display: flex;
    width: 190px;
    height: 72px;

    .scCategory {
      width: 190px;
      height: 72px;
      border: 1px solid;
      box-sizing: border-box;
      padding: 10px 10px 10px 20px;
      display: flex;
      align-items: center;
      font-weight: 500;
    }
  }
}
</style>
