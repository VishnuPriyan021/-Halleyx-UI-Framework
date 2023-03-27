<template>
  <nav class="breadcrumb">
    <ul>
      <li v-for="(item, index) in items" :key="index"  @click="current(item)">
      <i v-if="item.icon!=undefined" :class="item.icon" ></i>
      <div :class="{ disabledd: index === items.length - 1 } ">{{item.label}}</div>
        <!-- <router-link :to="item.link" :class="{ disabled: index === items.length - 1 } " >{{ item.label }}</router-link> -->
        <span v-if="index < items.length - 1" class="breadcrumb-separator">
          <i v-if="isIconSeparator" :class="separator.icon"></i>
          <span v-else>{{ separator }}</span>
        </span>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: 'hlx-breadcrumb',
  emits:["path"],
  props: {
    items: {
      type: Array,
      required: true
    },
    separator: {
      type: [String, Object],
      default: '/'
    }
  },
  computed: {
    isIconSeparator() {
      return typeof this.separator === 'object';
    }
  },
  methods:{
    current(item){
      this.$emit('path',item)
    }
  }
}
</script>

<style lang="scss">

</style>