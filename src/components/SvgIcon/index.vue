<template>
  <svg :style="iconStyle" aria-hidden="true">
    <use :xlink:href="symbolId" fill="red" />
  </svg>
</template>

<script setup lang="ts" name="SvgIcon">
import { computed, CSSProperties } from "vue";

interface SvgProps {
  name: string; // 图标的名称 ==> 必传
  prefix?: string; // 图标的前缀 ==> 非必传（默认为"icon"）
  iconStyle?: CSSProperties; // 图标的样式 ==> 非必传
}

const props = withDefaults(defineProps<SvgProps>(), {
  prefix: "icon",
  iconStyle: () => ({ width: "16px", height: "16px", fill: "#e4e6eb", color: "#e4e6eb" })
});

const symbolId = computed(() => `#${props.prefix}-${props.name}`);
</script>
