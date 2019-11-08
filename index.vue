<template>
  <ul class="vue-tabs">
    <li
      v-for="item in list"
      :key="item[props.id]"
      class="tabs__item"
      :style="{color: item[props.id] === currentActive ? activeColor :color,height: height +'px' }"
      @click="handleClick(item)"
      :ref="`tabsItem${item[props.id]}`"
    >
      <span>{{ item[props.label] }}</span>
    </li>
    <span class="tabs-line" ref="tabsLine" :style="{width: lineWidth +'px',transform: 'translateX(' + translateX + 'px)', 'background-color':activeColor }"></span>
  </ul>
</template>
<script>
export default {
  model: {
    prop: 'currentActive',
    event: 'input'
  },
  props:{
    list: {
      type: Array,
      default: () => []
    },
    currentActive: {
      type: Number | String,
      default: ''
    },
    props:{
      type: Object,
      default: () =>({
        label: 'label',
        id: 'id'
      })
    },
    activeColor: {
      type: String,
      default: 'blue'
    },
    color: {
      type: String,
      default: '#444'
    },
    height: {
      type: String | Number,
      default: 80
    },
  },
  data() {
    return {
      lineWidth: 0,
      translateX: 0
    };
  },
  mounted() {
    this.$nextTick(()=>{
      this.lineWidth = this.$refs["tabsItem" + this.currentActive][0].offsetWidth;
      this.translateX = this.$refs["tabsItem" + this.currentActive][0].offsetLeft
    })
  },
  methods: {
    handleClick(item){
      let current = item[this.props.id]
      this.$emit('input',current)
      this.$emit('click',item)
      this.lineWidth = this.$refs["tabsItem" + current][0].offsetWidth;
      this.translateX = this.$refs["tabsItem" + current][0].offsetLeft
    }
  },
};
</script>
<style lang="scss" scoped>
ul.vue-tabs {
  position: relative;
  display: flex;
}
li.tabs__item {
  margin-right: 40px;
  display: flex;
  align-items: center;
  cursor: pointer;
  &:last-of-type {
    margin-right: 0;
  }
}
.tabs-line {
  position: absolute;
  height: 4px;
  bottom: 0;
  left: 0;
  transition: .2s transform, width;
  z-index: 10;
}
</style>