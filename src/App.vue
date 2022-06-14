<script setup>
import { ref } from "vue";
import dayjs from "dayjs";
import botData from "@/assets/e.json";
const startTime = ref(botData.export_data[5687069307].start_at_str);
const endTime = ref(botData.export_data[5687069307].end_at_str);
const total = ref(botData.export_data[5687069307].total_export_mblog_count);
const bot = ref(botData.export_data[5687069307].record_list);
</script>

<template>
  <div class="header-info">
    <div>
      From {{ dayjs(startTime).format("YYYY年MM月DD日") }} to
      {{ dayjs(endTime).format("YYYY年MM月DD日") }}
    </div>
    <div>Total: {{ total }}</div>
  </div>
  <div class="bot-body">
    <div v-for="item of bot" :key="item.id" class="bot-card">
      <div v-html="item.text"></div>
      <div v-html="dayjs(item.created_at).format('YYYY年MM月DD日')"></div>
    </div>
  </div>
</template>

<style lang="scss">
#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;

  .bot-body {
    .bot-card {
      margin: 10px 0;
    }
  }
}
</style>
