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
           <audio :src="audioRequest" ref="audioRequest"></audio>
           <audio :src="audioCallback" ref="audioCallback"></audio>            
          </div>
        </card>
      </div>

    </div>
</template>
<script>
import { PaperTable, } from "@/components";
import axios from 'axios';
import audioRequest from "../assets/audio/数据协同请求.mp3";
import audioCallback from "../assets/audio/返回数据协同请求结果.mp3";

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
      this.$refs.audioRequest.play();

      axios({
        method:"get",
        url:"http://127.0.0.1:8080/datashare/query",
        params: {id: this.formData.id},
        headers: {
        "Content-Type": "multipart/form-data"
        },
        // withCredentials:true,
        // data:formData
      }).then((res)=>{
        var msg = res.data.Msg
        var msgJson = JSON.parse(msg)
        var output = "pm2.5: " + msgJson.result.pm.pm2_5
        alert(output)              

            this.$refs.audioCallback.play();    
      }); 


      // axios.get("http://127.0.0.1:8080/datashare/query",{params: {id: this.formData.id}})
      //   .then(res=>{
      //       console.log('res=>',res);      
      //       this.$refs.audioCallback.play();      
      //   })  
    },
  },
  data() {
    return {
      audioRequest: audioRequest,
      audioCallback: audioCallback,      
      table1: {
        title: "Stripped Table",
        subTitle: "Here is a subtitle for this table",
        columns: [...tableColumns],
        data: [...tableData]
      },
      formData: {
        id: "7",
        name: "ccc",
        type: "data",
        ip: "https://api.apishop.net/common/air/getCityPM25Detail?apiKey=SWj6Udr57f&city=北京市",
        route: "/111",
        abstract: "2asdswere",
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
