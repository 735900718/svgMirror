<template>
  <svg :width="width" :height="height * 2">
    <defs>
      <linearGradient :id="'gradient-' + _uid" x1="0" y1="0" x2="0" y2="1">
        <stop
          :offset="mask.offset"
          stop-color="#fff"
          :stop-opacity="mask.opacity"
          v-for="(mask, index) in maskStop"
          :key="index"
        />
      </linearGradient>
      <mask :id="'mask-' + _uid">
        <rect
          x="0"
          :y="height"
          :width="width"
          :height="height"
          :fill="`url(#${'gradient-' + _uid})`"
        />
      </mask>
      <pattern
        :id="'reflect-' + _uid"
        patternUnits="userSpaceOnUse"
        :width="width"
        :height="height"
      >
        <image :xlink:href="image" :width="width" :height="height" />
      </pattern>
    </defs>
    <!-- 原图 -->
    <rect
      x="0"
      y="0"
      :width="width"
      :height="height"
      :fill="`url(#${'reflect-' + _uid})`"
    ></rect>
    <!-- 倒影图 -->
    <rect
      x="0"
      :y="height"
      :width="width"
      :height="height"
      :fill="`url(#${'reflect-' + _uid})`"
      :mask="`url(#${'mask-' + _uid})`"
      :transform="
        `translate(${width / 2} ${height}) scale(1, -1) translate(-${width /
          2} -${height * 2 + gap})`
      "
    ></rect>
  </svg>
</template>

<script>
export default {
  name: "Mirror",
  props: {
    width: {
      type: Number,
      default: 128,
    },
    height: {
      type: Number,
      default: 128,
    },
    gap: {
      type: Number,
      default: 5,
    },
    image: {
      type: String,
      default: "",
    },
    maskStop: {
      type: Array,
      default: function() {
        return [
          { offset: "0%", opacity: "0" },
          { offset: "100%", opacity: "1" },
        ];
      },
    },
  },
};
</script>
