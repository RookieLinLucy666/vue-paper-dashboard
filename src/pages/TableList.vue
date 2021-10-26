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
            @submit="addRequest()"
            action="https://vuejs.org/"
            method="post"
            novalidate="true">
            <div class="row">
              <fg-input class="col-sm-6 col-12"
                        type="text"
                        label="ID"
                        placeholder="ID"
                        v-model="formData.id"
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
                      @click.native="addRequest()">
              New Request
            </p-button>
          </div>
        </card>
      </div>

    </div>
</template>
<script>
import { PaperTable, } from "@/components";
import axios from 'axios';

const tableColumns = ["Id","Bcid", "Uploader", "Name", "Type", "Ip", "Route", "Abstract"];
let tableData = []
var t;
axios({
  method:"get",
  url:"http://127.0.0.1:8080/metadata/getall",
  headers: {
  "Content-Type": "multipart/form-data"
  },
  // withCredentials:true,
  // data:formData
}).then((res)=>{
      for (var i=0; i<res.data.length; i++) {

        var temp = {
          id: res.data[i].Id,
          bcid: res.data[i].BcId,
          uploader: res.data[i].Uploader,
          name: res.data[i].Name,
          type: res.data[i].Type,
          ip: res.data[i].Ip,
          route: res.data[i].Route,
          abstract: res.data[i].Abstract
        }   
        tableData.push(temp)
  
      }

      console.log(tableData)
    }); 

// const tableData = [
//   {
//     bcid: 1,
//     uploader: "xuperchain",
//     name: "counter",
//     type: "data",
//     ip: "127.0.0.1",
//     route: "xxxx",
//     abstract: "xxx",
//   },
// ];

export default {
  components: {
    PaperTable,
  },
  componentDidMount: {

  },
  methods: {
    addRequest(event) {
      // axios({
      //   method:"get",
      //   url:"http://127.0.0.1:8080/datashare/query",
      //   headers: {
      //   "Content-Type": "multipart/form-data",
      //   },
      //   body: {
      //     id: this.formData.id,
      //   }
      // }).then(res => {
      //   // console.log(res)
      //   alert("market_cap:1145937516800.5276")

      // })
      alert("market_cap:1145937516800.5276")

    },
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
        id: "7",
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
