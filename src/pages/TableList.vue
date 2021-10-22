<template>
    <div class="row" style="height: 580px">
      <div class="col-12">
        <card :title="table1.title" :subTitle="table1.subTitle">
          <div slot="raw-content" class="table-responsive">
            <paper-table :data="table1.data" :columns="table1.columns">
            </paper-table>
          </div>
        </card>
      </div>

      <div style="width:100%; height:auto; float:left; display:block">
        <card class="architecture-graph"  style="width: 100%; height: auto;max-width: 100%; display: block;">
          <form id="app"
            @submit="addRequest"
            action="https://vuejs.org/"
            method="post"
            novalidate="true">
            <div class="row">
              <fg-input class="col-sm-6 col-12"
                        type="text"
                        label="Uploader"
                        placeholder="Uploader"
                        v-model="formData.uploader"
                        >
              </fg-input>
              <fg-input class="col-sm-6 col-12"
                        type="text"
                        label="Name"
                        placeholder="Name"
                        v-model="formData.name"
                        >
              </fg-input>
            </div>
            <div class="row">
              <fg-input class="col-sm-6 col-12"
                        type="text"
                        label="Type"
                        placeholder="Type"
                        v-model="formData.type"
                        >
              </fg-input>
              <fg-input class="col-sm-6 col-12"
                        type="text"
                        label="Ip"
                        placeholder="Ip"
                        v-model="formData.ip"
                        >
              </fg-input>
            </div>
            <div class="row">
              <fg-input class="col-sm-6 col-12"
                        type="text"
                        label="Route"
                        placeholder="Route"
                        v-model="formData.route"
                        >
              </fg-input>
              <fg-input class="col-sm-6 col-12"
                        type="text"
                        label="Abstract"
                        placeholder="Abstract"
                        v-model="formData.abstract"
                        >
              </fg-input>
            </div>
          </form>
          <div class="text-center">
            <p-button type="info"
                      round
                      @click="addRequest()">
              New Request
            </p-button>
          </div>
        </card>
      </div>

    </div>
</template>
<script>
import { PaperTable, } from "@/components";
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
  },
  methods: {
    addRequest(event) {
      console.log("aaa")
    }
  },
  data() {
    return {
      table1: {
        title: "Stripped Table",
        subTitle: "Here is a subtitle for this table",
        columns: [...tableColumns],
        data: [...tableData]
      },
      formData: {
        uploader: "xuperchain",
        name: "counter",
        type: "data",
        ip: "https://pro-api.coinmarketcap.com/v1/cryptocurrency/listings/latest",
        route: "xuperchain",
        abstract: "162accb12e079d4b805f65f7a773c5e10cf537fef5ff99fde901ef0b1c963af8",
      }
      // table2: {
      //   title: "Table on Plain Background",
      //   subTitle: "Here is a subtitle for this table",
      //   columns: [...tableColumns],
      //   data: [...tableData]
      // }
    };
  },
};
</script>
<style>
</style>
