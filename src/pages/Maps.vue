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
        </form>
          <div class="col-md-5" >
            <fg-input type="text"
                      label="Model"
                      placeholder=""
                      v-model="model"
                      style="width: 100px;">
            </fg-input>
            <fg-input type="text"
                      label="Dataset"
                      placeholder=""
                      v-model="dataset"
                      style="width: 100px;">
            </fg-input>
            <fg-input type="text"
                      label="Epoch"
                      placeholder=""
                      v-model="epoch"
                      style="width: 100px;">
            </fg-input>
            <fg-input type="text"
                      label="round"
                      placeholder=""
                      v-model="round"
                      style="width: 100px;">
            </fg-input>                                    
          </div>        

        <div class="text-center">
          <p-button type="info"
                    round
                    @click.native.prevent="addRequest">
            New Request
          </p-button>
        </div>          
      </card>      
    </div>
  </div>
</template>
<script>
import { PaperTable, } from "@/components";

export default {

  components: {
    PaperTable,
  },

  data() {
    return {
      model:"cnn",
      dataset: "mnist",
      epoch: 1,
      round: 1,
    }
  },

  methods: {
    addRequest(event) {
      console.log(event)
    }
  }

};
</script>
<style>
.col-md-5 {
  width:10px;
}
</style>
