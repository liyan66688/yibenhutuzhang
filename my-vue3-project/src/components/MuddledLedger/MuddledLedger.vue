<script setup>

import {ref} from "vue";
import LedgerTab from "@/components/MuddledLedger/LedgerTab.vue";
import Consumption from "@/components/MuddledLedger/Consumption.vue";
import Category from "@/components/MuddledLedger/Category.vue";
import Record from "@/components/MuddledLedger/Record.vue";
import Report from "@/components/MuddledLedger/Report.vue";

const cur_page = ref("consumption");
function set_cur_page(val) {
  cur_page.value = val
}
</script>

<template>
  <div>
    <LedgerTab
        @consumption="set_cur_page('consumption')"
        @note="set_cur_page('note')"
        @classify="set_cur_page('classify')"
        @report="set_cur_page('report')"
        @setting="set_cur_page('setting')"
    ></LedgerTab>
  </div>
  <div>
    <Consumption v-if="cur_page==='consumption'"></Consumption>
    <Category  v-else-if="cur_page==='classify'"></Category>
    <Record  v-else-if="cur_page==='note'"></Record>
    <Report  v-else-if="cur_page==='report'"></Report>
  </div>
</template>

<style scoped>

</style>