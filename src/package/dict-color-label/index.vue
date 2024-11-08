<!-- 普通的回显文本，带颜色，如果有值，则回显，没有值则显示数字 -->
<template>
  <div>
    <template v-if="valueList.includes(String(this.value))">
      <template v-for="(item, index) in options">
        <span
          v-if="value == item.value"
          :key="item.value + index"
          :style="{ color: typeList.includes(item.type) ? colorList[item.type] : item.color }"
        >{{ item.label || item.value }}</span>
      </template>
    </template>
    <template v-else>
      <span>{{ emptyText === '-' ? value : emptyText }}</span>
    </template>
  </div>
</template>

<script>
export default {
  name: "OptionsDict",
  props: {
    // 需要回显的数组，格式为：[{value: '1', label: '男', type: 'success'}, {value: '2', label: '女'}]
    options: {
      type: Array,
      default: null,
    },
    // 回显值
    value: [Number, String],
    // 没有对应回显的，显示的文本
    emptyText: {
      type: String,
      default: '-'
    }
  },

  computed: {
    valueList() {
      return this.options.map(item => String(item.value))
    }
  },

  data() {
    return {
      typeList: [ 'primary','success', 'warning', 'danger', 'info' ],
      colorList: {
        primary: '#3790FF',
        success: '#39C87D',
        warning: '#FFA912',
        danger: '#FF4A41',
        info: '#BABABA',
      }
    };
  },
};
</script>
