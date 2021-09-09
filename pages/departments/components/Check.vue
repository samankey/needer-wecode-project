<template>
  <div class="checkboxCon">
    <!-- Check All -->
    <div class="hoverBackground">
      <label class="checkAllWrap">
        Check All
        <label class="switch" for="toggle">
          <input
            id="toggle"
            v-model="isCheckAll"
            class="allInput"
            type="checkbox"
            @click="checkAll()"
          />
          <div class="slider round"></div>
        </label>
      </label>
    </div>
    <div class="separate"></div>
    <!-- Checkboxes list -->
    <label class="hoverBackground" for="toggleList">
      <label v-for="lang in langsdata" :key="lang" class="checkboxList">
        {{ lang }}
        <label class="switch">
          <input
            id="toggleList"
            v-model="languages"
            class="listInput"
            type="checkbox"
            :value="lang"
            @change="updateCheckall()"
          />
          <span class="slider round"></span>
        </label>
      </label>
    </label>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      isCheckAll: false,
      langsdata: ['근무', '휴무'],
      languages: [],
      selectedlang: '',
    }
  },
  methods: {
    checkAll() {
      this.isCheckAll = !this.isCheckAll
      this.languages = []
      if (this.isCheckAll) {
        // Check all
        for (const key in this.langsdata) {
          this.languages.push(this.langsdata[key])
        }
      }
    },
    updateCheckall() {
      if (this.languages.length === this.langsdata.length) {
        this.isCheckAll = true
      } else {
        this.isCheckAll = false
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.hoverBackground {
  :hover {
    background-color: #f7f8f8;
  }
}

.checkboxCon {
  position: absolute;
  width: 200px;
  border-radius: 5px;
  padding: 8px;
  background-color: rgb(255, 255, 255);
  overflow: hidden;
}

.checkAllWrap {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
  cursor: pointer;
}

.checkBoxWrap {
  border-radius: 8px;
  background: seagreen;
  width: 200px;
}

.checkboxList {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 8px;
  cursor: pointer;

  .listInput {
    top: 0px;
    right: 0px;
    cursor: pointer;
  }
}

.checkBoxWrap {
  display: inline;
}

// 밑에서 부터 토글 기능

.switch {
  position: relative;
  display: inline-block;
  width: 42px;
  height: 20.4px;

  /* .switchInput {
    opacity: 0;
  } */
}

.slider {
  position: absolute;
  cursor: pointer;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: #ccc;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

.slider:before {
  position: absolute;
  content: '';
  height: 15.6px;
  width: 15.6px;
  left: 2.4px;
  bottom: 2.4px;
  background-color: white;
  -webkit-transition: 0.4s;
  transition: 0.4s;
}

input:checked + .slider {
  background-color: #2196f3;
}

input:focus + .slider {
  box-shadow: 0 0 1px #2196f3;
}

input:checked + .slider::before {
  -webkit-transform: translateX(22px);
  -ms-transform: translateX(22px);
  transform: translateX(22px);
}

.slider.round {
  display: block;
  border-radius: 34px;
}

.slider.round:before {
  border-radius: 50%;
}

.separate {
  border-top: 1px solid;
  margin: 8px 0 8px 0;
}
</style>
