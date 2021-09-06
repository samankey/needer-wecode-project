<template>
  <div>
    <div class="checkBoxWrap">
      <div id="myapp">
        <!-- Check All -->
        <div class="checkAllWrap">
          <input
            v-model="isCheckAll"
            type="checkbox"
            @click="checkAll()"
          />Check All
        </div>
        <CheckBox />
        <!-- Checkboxes list -->
        <ul>
          <li v-for="lang in langsdata" :key="lang">
            <input
              v-model="languages"
              type="checkbox"
              :value="lang"
              @change="updateCheckall()"
            />{{ lang }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import CheckBox from './CheckBox.vue'

export default {
  components: {
    CheckBox,
  },
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
.checkBoxWrap {
  width: 200px;
  border-radius: 8px;
  padding: 10px;
  background: seagreen;
}
</style>
