<template>
<!--  <card class="card-user">-->
    <div class="col-12">
      <card class="architecture"  style="width: 100%; height: auto;max-width: 100%; display: block;">     
        <form id="app"
          @submit="addRequest"
          action="https://vuejs.org/"
          method="post"
          novalidate="true">
          <div class="row">
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="Name"
                      placeholder=""
                      v-model="identity.name"
                      >
            </fg-input>
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="Abstract"
                      placeholder=""
                      v-model="identity.abstract"
                      >
            </fg-input>                        
          </div>
        </form>
        <div class="text-center">
          <p-button type="info"
                    round
                    @click.native="addUser">
            Authorization
          </p-button>

          <span></span>

          <p-button type="info"
                    round
                    @click.native="checkUser">
            Verification
          </p-button>

           <audio :src="audioRequest" ref="audioRequest"></audio>
           <audio :src="audioCallback" ref="audioCallback"></audio>

        </div>
      </card>
    </div>     
<!--  </card>-->
</template>
<script>
import { PaperTable, } from "@/components";
import audioRequest from "../../assets/audio/身份认证请求上链.mp3";
import audioCallback from "../../assets/audio/返回身份认证结果.mp3";
import axios from 'axios';

export default {
  components: {
    PaperTable,
  },
  methods: {
    addUser() {
    this.$refs.audioRequest.play();
    axios.post("http://127.0.0.1:8080/identify/adduser",this.identify)
      .then(res=>{
          // alert(res.config.data)   
          console.log(res)  
          this.$refs.audioCallback.play();                      
      }) 
    },
    checkUser() {
    this.$refs.audioRequest.play();
    axios.post("http://127.0.0.1:8080/identify/checkuser",this.identify)
      .then(res=>{
          alert(res)   
          console.log(res) 
          this.$refs.audioCallback.play();                       
      })   
    }
  },
  /**
   * Chart data used to render stats, charts. Should be replaced with server data
   */
  data() {
    return {
      audioRequest: audioRequest,
      audioCallback: audioCallback,      
      identity: {
        name: "Alice",
        abstract: "ezDq8L2yHpqTSmKFs3HCiFmVELN67hFF3",
      }
    };
  }
};
</script>
<style>
</style>
