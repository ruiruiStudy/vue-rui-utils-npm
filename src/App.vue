<template>
  <div id="app">
    <!--  默认回显  -->
    <dict-color-label :options="auditStatusOptions" :value="1" />
    <dict-color-label :options="auditStatusOptions" :value="0" />
    <!--  找不到值的，默认显示value  -->
    <dict-color-label :options="auditStatusOptions" :value="2" />
    <!--  找不到值的，也可传入显示的文本  -->
    <dict-color-label :options="auditStatusOptions" :value="3" empty-text="//" />
    <!--  支持自定义颜色 color  -->
    <dict-color-label :options="auditStatusOptions" :value="5" />
    <!--  不传颜色  -->
    <dict-color-label :options="auditStatusOptions" :value="6" />
  </div>
</template>

<script>
import { DictColorLabel } from './package'
export default {
  name: 'App',
  components: {
    DictColorLabel
  },
  data() {
    return {
      auditStatusOptions: [
        { value: '0', label: '有值：未审核', type: 'warning' },
        { value: '1', label: '有值：已审核', type: 'success' },
        { value: '5', label: '自定义颜色', color: 'red' },
        { value: '6', label: '无颜色', },
      ]
    }
  }
}
</script>

<style>

</style>
