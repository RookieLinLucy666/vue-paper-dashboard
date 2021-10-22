<template>
  <div style="height: 580px;display: block;"> 
    <div style="width:500px; margin-left:40px; height:auto; float:left; display:block">
      <card class="architecture-graph" title="Architecture Graph" style="width: 100%; height: auto;max-width: 100%; display: block;">
        <div class="computing-img">
            <img style="width: 100%; height: auto;max-width: 100%; display: block;" src="@/assets/img/architecture.png" alt="">
        </div>
      </card>
    </div>

    <div style="width:500px; margin-left:40px;height:auto; float:left; display:block">
      <card class="computing-graph" title="Computing Graph" style="width: 100%; height: auto;max-width: 100%; display: block;">
      <div class="computing-img">
          <img style="width: 100%; height: auto;max-width: 100%; display: block;" src="@/assets/img/computing.png" alt="">
      </div>
    </card>
    </div>

    <div style="width:100%; margin-left:40px;height:auto; float:left; display:block">
      <card class="architecture-graph"  style="width: 100%; height: auto;max-width: 100%; display: block;">
        <form id="app"
          @submit="addRequest"
          action="https://vuejs.org/"
          method="post"
          novalidate="true">
          <fg-input type="text"
                    label="Model"
                    placeholder=""
                    v-model="formData.model"
                    >
          </fg-input>            

          <fg-input type="text"
                    label="Dataset"
                    placeholder=""
                    v-model="formData.dataset"
                    >
          </fg-input>
          <fg-input type="text"
                    label="Epoch"
                    placeholder=""
                    v-model="formData.epoch"
                    >
          </fg-input>
          <fg-input type="text"
                    label="round"
                    placeholder=""
                    v-model="formData.round"
                    >
          </fg-input>   
        </form>  
        <p-button type="info"
                  round
                  @click="addRequest()">
          New Request
        </p-button>                                 
      </card>      
    </div>
  </div>
</template>
<script>
import { PaperTable, } from "@/components";
import axios from 'axios';

export default {

  components: {
    PaperTable,
  },

  data() {
    return {
      formData: {
        model:"cnn",
        dataset: "mnist",
        epoch: 1,
        round: 1,
      }
    }
  },

  methods: {
    addRequest(event) {
      let formData = new FormData();
      for(var key in this.formData) {
        formData.add(key, this.formData[key]);
      }
      axios({
        method:"post",
        url:"xxxxxxx",
        headers: {
        "Content-Type": "multipart/form-data"
        },
        withCredentials:true,
        data:formData
      }).then((res)=>{
            console.log(res);
          });
    }
  }

};
</script>
<style>
.col-md-5 {
  width:10px;
}
</style>
