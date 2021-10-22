<template>
    <div class="row">
      <div class="col-12">
        <card :title="table1.title" :subTitle="table1.subTitle">
          <div slot="raw-content" class="table-responsive">
            <paper-table :data="table1.data" :columns="table1.columns">
            </paper-table>
          </div>
        </card>
      </div>

      <PButton></PButton>

<!--       <div class="col-12">
        <card class="card-plain">
          <div class="table-full-width table-responsive">
            <paper-table type="hover" :title="table2.title" :sub-title="table2.subTitle" :data="table2.data"
                         :columns="table2.columns">

            </paper-table>
          </div>
        </card>
      </div> -->

    </div>
</template>
<script>
import { PaperTable, PButton } from "@/components";
const tableColumns = ["Id", "Address", "API", "Result"];
const tableData = [
  {
    id: 1,
    address: "ezDq8L2yHpqTSmKFs3HCiFmVELN67hFF3",
    api: "https://pro-api.coinmarketcap.com/v1/listings/latest",
    result: "$66352"
  },
  {
    id: 2,
    address: "jPSFQjS6jwMi8tU8F2EFLAiWXpMGno4FU",
    api: "$http://mobile.weather.com.cn/data/forecast/101010100.html?_=1381891660081",
    result: "13℃"
  },
  {
    id: 3,
    address: "nuSMPvo6UUoTaT8mMQmHbfiRbJNbAymGh",
    api: "$http://tj.nineton.cn/Heart/index/all",
    result: "Rainy"
  },
];

export default {
  components: {
    PaperTable,
    PButton,
  },
  data() {
    return {
      table1: {
        title: "Stripped Table",
        subTitle: "Here is a subtitle for this table",
        columns: [...tableColumns],
        data: [...tableData]
      },
      // table2: {
      //   title: "Table on Plain Background",
      //   subTitle: "Here is a subtitle for this table",
      //   columns: [...tableColumns],
      //   data: [...tableData]
      // }
    };
  }
};
</script>
<style>
</style>
