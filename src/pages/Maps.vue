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
          <div class="row">
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="Bcid"
                      placeholder=""
                      v-model="formData.bcid"
                      >
            </fg-input>
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="Type"
                      placeholder=""
                      v-model="formData.type"
                      >
            </fg-input>                        
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="Model"
                      placeholder=""
                      v-model="formData.model"
                      >
            </fg-input>
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="Dataset"
                      placeholder=""
                      v-model="formData.dataset"
                      >
            </fg-input>
          </div>
          <div class="row">
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="Epoch"
                      placeholder=""
                      v-model="formData.epoch"
                      >
            </fg-input>
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="round"
                      placeholder=""
                      v-model="formData.round"
                      >
            </fg-input>
          </div>
        </form>
        <div class="text-center">
          <p-button type="info"
                    round
                    @click.native="addRequest">
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
import audioRequest from "../assets/audio/计算协同请求.mp3";
import audioCallback from "../assets/audio/返回计算协同请求结果.mp3";

let sleepFun = function(fun, time) {
  setTimeout(function() {
    fun();
  }, time);
}
export default {

  components: {
    PaperTable,
  },

  data() {
    return {
      audioRequest: audioRequest,
      audioCallback: audioCallback,
      formData: {
        bcid: "CarFileAssetId_59",
        type: "compute",
        model:"cnn",
        dataset: "mnist",
        epoch: 1,
        round: 1,
      },
      identify: {
        name: "asasdas",
        abstract: "ashdklasd"
      },
    }
  },

  methods: {
    addRequest(event) {
    this.$refs.audioRequest.play();
      alert("accuracy: 92.48%")

    axios.post("http://127.0.0.1:8080/datashare/computingshare",this.formData)
      .then(res=>{
          console.log('res=>',res);      
          this.$refs.audioCallback.play();      
      })  
},

palyAudio(){
    this.audio = new Audio("@assets/audio/身份认证请求上链.mp3");
    this.audio.src = mp3;
    let playPromise; 
    playPromise = this.audio.play();
    if (playPromise) {
        playPromise.then(() => {
            // 音频加载成功
            // 音频的播放需要耗时
          that.tiemr = setInterval(() => {
            second--;
            if (second <= 0) {
              that.audio.pause()
              clearInterval(that.tiemr);
            }
          }, 1000);
        }).catch((e) => {
          // 音频加载失败
          console.error(e);
        });
      }
  },


  }

};
</script>
<style>
.col-md-5 {
  width:10px;
}
</style>
