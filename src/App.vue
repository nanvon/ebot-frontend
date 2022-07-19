<script setup>
import { ref } from "vue";
import dayjs from "dayjs";
import botData from "@/assets/e.json";
const startTime = ref(botData.export_data[5687069307].start_at_str);
const endTime = ref(botData.export_data[5687069307].end_at_str);
const total = ref(botData.export_data[5687069307].total_export_mblog_count);
const bot = ref(botData.export_data[5687069307].record_list);
const botPageData = ref({});
botPageData.value = bot.value.slice(0, 10);

const currentPage = ref(1);
const pageSize = ref(10);

const handleSizeChange = (val) => {
  botPageData.value = bot.value.slice((currentPage.value - 1) * val, currentPage.value * val);
}
const handleCurrentChange = (val) => {
  botPageData.value = bot.value.slice((val - 1) * pageSize.value, val * pageSize.value);
}
</script>

<template>
  <el-pagination
                 v-model:currentPage="currentPage"
                 v-model:page-size="pageSize"
                 :page-sizes="[10, 20, 50, 100]"
                 layout="jumper, prev, pager, next, sizes, total"
                 :total="total"
                 @size-change="handleSizeChange"
                 @current-change="handleCurrentChange"
                 class="pagination" />
  <el-card class="box-card" v-for="item of botPageData" :key="item.id">
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
  .pagination {
    display: flex;
    justify-content: center;
    margin: 20px 0;
  }

  @media (max-width: 700px) {
    .pagination {
      flex-direction: column;
    }
  }

  .box-card {
    max-width: 1280px;
    margin: 0 auto;
    padding: 2rem;
    font-weight: normal;
    margin-bottom: 10px;
  }
}
</style>
