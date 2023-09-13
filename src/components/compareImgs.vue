<template>
  <article class="container mx-auto">
    <form action="#" class="grid grid-cols-2 py-4">
      <fieldset class="border-r">
        <table class="mx-auto">
          <caption class="pb-3">
            左圖設置
          </caption>
          <tbody>
            <tr>
              <td>明亮度</td>
              <td class="text-right">
                <input v-model="left.brightness" type="number" min="0" max="200" class="input" />%
              </td>
              <td><input v-model="left.brightness" type="range" min="0" max="200" /></td>
            </tr>
            <tr>
              <td>對比度</td>
              <td class="text-right">
                <input v-model="left.contrast" type="number" min="0" max="200" class="input" />%
              </td>
              <td><input v-model="left.contrast" type="range" min="0" max="200" /></td>
            </tr>
            <tr>
              <td>透明度</td>
              <td class="text-right">
                <input v-model="left.opacity" type="number" min="0" max="100" class="input" />%
              </td>
              <td><input v-model="left.opacity" type="range" min="0" max="100" /></td>
            </tr>
          </tbody>
        </table>
      </fieldset>
      <fieldset>
        <table class="mx-auto">
          <caption class="pb-3">
            右圖設置
          </caption>
          <tbody>
            <tr>
              <td>明亮度</td>
              <td class="text-right">
                <input v-model="right.brightness" type="number" min="0" max="200" class="input" />%
              </td>
              <td><input v-model="right.brightness" type="range" min="0" max="200" /></td>
            </tr>
            <tr>
              <td>對比度</td>
              <td class="text-right">
                <input v-model="right.contrast" type="number" min="0" max="200" class="input" />%
              </td>
              <td><input v-model="right.contrast" type="range" min="0" max="200" /></td>
            </tr>
            <tr>
              <td>透明度</td>
              <td class="text-right">
                <input v-model="right.opacity" type="number" min="0" max="100" class="input" />%
              </td>
              <td><input v-model="right.opacity" type="range" min="0" max="100" /></td>
            </tr>
          </tbody>
        </table>
      </fieldset>
    </form>

    <div class="text-center">
      <ImgComparisonSlider>
        <!-- eslint-disable -->
        <img slot="first" src="@/assets/image/before.webp" :style="styleLeft" />
        <img slot="second" src="@/assets/image/after.webp" :style="styleRight" />
        <!-- eslint-enable -->
      </ImgComparisonSlider>
    </div>
  </article>
</template>

<script lang="ts" setup>
import { ImgComparisonSlider } from '@img-comparison-slider/vue';
import { computed, ref } from 'vue';

type image = {
  // 0% to 200% start from 100 = 100%
  brightness: number;
  // 0% to 200% start from 100 = 100%
  contrast: number;
  // 0% to 100% start from 100 = 100%
  opacity: number;
};

const left = ref<image>({
  brightness: 100,
  contrast: 100,
  opacity: 100
});
const right = ref<image>({
  brightness: 100,
  contrast: 100,
  opacity: 100
});

const styleLeft = computed(() => {
  return `filter: brightness(${left.value.brightness}%) contrast(${left.value.contrast}%) opacity(${left.value.opacity}%)`;
});
const styleRight = computed(() => {
  return {};
});
</script>

<style>
td {
  @apply px-1 py-1;
}

.input {
  @apply mr-1 rounded border border-white/25 bg-transparent px-1 py-1 text-right;
}
</style>
