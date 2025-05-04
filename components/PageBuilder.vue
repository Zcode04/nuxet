<script lang="ts" setup>
import type { PageQueryResult } from "~/sanity/types";

type PageBuilderBlock = NonNullable<
  NonNullable<PageQueryResult>["pageBuilder"]
>[number];

defineProps({
  blocks: {
    type: Array as () => PageBuilderBlock[],
    required: false,
  },
});
</script>

<template>
  <component
    v-for="(block, index) in blocks"
    :key="block._key"
    :is="resolveComponent(block._type) || 'div'"
    :block="block"
  >
    <div v-if="!resolveComponent(block._type)">
     كنكوصه ميديا نسخ تجريبية
    </div>
  </component>
</template>
