<template>
    <div v-for="(item, index) in this.data" :key="index" :class="this.show === true ? 'parent' : ''">
        <div class="db-row" id="obj" v-if="this.type === 'read-only'">
            <div v-if="typeof item === 'object'" class="array-index-parent">
                <span v-if="typeof index === 'number'" class="array-index">{{index + ': '}}</span>
                <span v-if="typeof index === 'string'" class="array-string">{{index}}</span>
            </div>
            <div v-if="typeof item === 'object'" class="div-with-arrow"  >
              <i v-if="Array.isArray(this.data)" :class="this.showArray[index] ? 'icon-angle-right-regular' : 'icon-angle-down-regular'" @click="this.showChildFunc(index)"></i>
                <i v-else :class="this.showChild[index] ? 'icon-angle-right-regular' : 'icon-angle-down-regular'" @click="this.showChildFunc(index)"></i>  <mongo-db-record :data="item" :show="Array.isArray(this.data) ? this.showArray[index] : this.showChild[index]" :type="'read-only'"></mongo-db-record>
            </div>
        </div>
        <div class="db-row" id="other" v-if="this.type === 'read-only'">
            <div v-if="typeof item === 'string' || typeof item === 'number'" class="colon-key">{{index}}</div>
            <div v-if="typeof item === 'string'" class="colon-value">{{item}}</div>
            <div v-if="typeof item === 'number'" class="colon-value">{{item}}</div>
        </div>
    </div>
</template>

<script>

export default {
  name: 'mongo-db-record',
  props: {
    data: {
      type: [Object, Array]
    },
    show: {
      type: Boolean,
      default: false
    },
    type: {
      type: String,
      default: 'read-only'
    }
  },
  data () {
    return {
      showChild: {},
      showArray: []
    }
  },
  mounted () {
    if (document.querySelector('.array-index-parent').children[0].classList.contains('array-index')) {
      document.querySelector('.array-index-parent').style.borderRight = '1px solid #d8d8d8'
    }
    if (Array.isArray(this.data)) {
      for (let index = 0; index < this.data.length; index++) {
        this.showArray.push(true)
      }
    } else {
      for (const index in this.data) {
        if (typeof (this.data[index]) === 'object') {
          this.showChild[index] = true
        }
      }
    }
  },
  methods: {
    showChildFunc (val) {
      if (Array.isArray(this.data)) {
        if (this.showArray[val] === true) {
          this.showArray[val] = false
        } else {
          this.showArray[val] = true
        }
      } else {
        const i = val
        if (this.showChild[i] === true) {
          this.showChild[i] = false
        } else {
          this.showChild[i] = true
        }
      }
    }
  }
}
</script>

<style></style>
