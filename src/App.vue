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
  <el-card class="box-card" v-for="item of bot" :key="item.id">
    <template #header>
      <div class="card-header">
        <span>{{ dayjs(item.created_at).format('YYYY年MM月DD日') }}</span>
      </div>
    </template>
    <div v-html="item.text"></div>
  </el-card>
</template>

<style lang="scss">
#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;
  font-weight: normal;

  .box-card {
    margin-bottom: 10px;
  }
}
</style>
