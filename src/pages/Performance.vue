<template>
  <div>

    <div class="form">
      <card class="architecture-graph"  >     
        <form id="app"
          @submit="presentResult"
          action="https://vuejs.org/"
          method="post"
          novalidate="true">
          <div class="row">
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="Type"
                      placeholder=""
                      v-model="request.type"
                      >
            </fg-input> 
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="Malicious Proportion"
                      placeholder=""
                      v-model="request.malicious"
                      >
            </fg-input>              
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="Dataset"
                      placeholder=""
                      v-model="request.dataset"
                      >
            </fg-input>            
   
            <fg-input class="col-sm-6 col-12"
                      type="text"
                      label="Node Count"
                      placeholder=""
                      v-model="request.nodeCount"
                      >
            </fg-input>                                                       
          </div>
          <div class="text-center">
            <p-button type="info"
                      round
                      @click.native="presentResult">
              New Request
            </p-button>
          </div>                   
        </form>
      </card>
    </div>      

    <!--Charts-->
    <div class="row">
      <div v-if="request.nodeCount==21" class="col-md-6 col-12">
        <chart-card title="Collaboration Performance"
                    sub-title="Collaboration time when node=21"
                    :chart-data="collaborationChart_21.data"
                    :chart-options="collaborationChart_21.options">
          <span slot="footer">
            <i class="ti-check"></i> Data information certified
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Data Collaboration
            <i class="fa fa-circle text-warning"></i> RIBFT
            <i class="fa fa-circle text-danger"></i> DBFT             
          </div>
        </chart-card>
      </div>

      <div v-if="request.nodeCount==24" class="col-md-6 col-12">
        <chart-card title="Collaboration Performance"
                    sub-title="Collaboration time when node=24"
                    :chart-data="collaborationChart_24.data"
                    :chart-options="collaborationChart_24.options">
          <span slot="footer">
            <i class="ti-check"></i> Data information certified
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Data Collaboration
            <i class="fa fa-circle text-warning"></i> RIBFT
            <i class="fa fa-circle text-danger"></i> DBFT             
          </div>
        </chart-card>
      </div>     

      <div v-if="request.nodeCount==27"  class="col-md-6 col-12">
        <chart-card title="Collaboration Performance"
                    sub-title="Collaboration time when node=27"
                    :chart-data="collaborationChart_27.data"
                    :chart-options="collaborationChart_27.options">
          <span slot="footer">
            <i class="ti-check"></i> Data information certified
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Data Collaboration
            <i class="fa fa-circle text-warning"></i> RIBFT
            <i class="fa fa-circle text-danger"></i> DBFT             
          </div>
        </chart-card>
      </div>

      <div v-if="request.malicious==10" class="col-md-6 col-12">
        <chart-card title="Accuracy Performance"
                    sub-title="Accuracy in Non-IID FMNIST dataset when malicious=10%"
                    :chart-data="accuracyChart_10.data"
                    :chart-options="accuracyChart_10.options">
          <span slot="footer">
            <i class="ti-check"></i> Data information certified
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Computing Collaboration
            <i class="fa fa-circle text-warning"></i> FedAvg
            <i class="fa fa-circle text-danger"></i> Proof                  
          </div>
        </chart-card>
      </div>       

      <div v-if="request.malicious==20" class="col-md-6 col-12">
        <chart-card title="Accuracy Performance"
                    sub-title="Accuracy in Non-IID FMNIST dataset when malicious=20%"
                    :chart-data="accuracyChart_20.data"
                    :chart-options="accuracyChart_20.options">
          <span slot="footer">
            <i class="ti-check"></i> Data information certified
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Computing Collaboration
            <i class="fa fa-circle text-warning"></i> FedAvg
            <i class="fa fa-circle text-danger"></i> Proof                  
          </div>
        </chart-card>
      </div>       

      <div v-if="request.malicious==30" class="col-md-6 col-12">
        <chart-card title="Accuracy Performance"
                    sub-title="Accuracy in Non-IID FMNIST dataset when malicious=30%"
                    :chart-data="accuracyChart_30.data"
                    :chart-options="accuracyChart_30.options">
          <span slot="footer">
            <i class="ti-check"></i> Data information certified
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Computing Collaboration
            <i class="fa fa-circle text-warning"></i> FedAvg
            <i class="fa fa-circle text-danger"></i> Proof                  
          </div>
        </chart-card>
      </div>
    </div>
  </div>
</template>
<script>
import { StatsCard, ChartCard } from "@/components/index";
import Chartist from 'chartist';
//http请求所需包  需要安装npm install --save axios
import axios from 'axios';

export default {
  components: {
    StatsCard,
    ChartCard
  },
  /**
   * Http请求，get/post方法
   */
  methods:{
    // get:function(){
    //   console.log('get请求方法');
    //   //发送get请求
    //   axios.get('http://127.0.0.1:8080/metadata/getall')
    //     .then(reponse=>{
    //       console.log(reponse.data)
    //     }).catch(function (error) {
    //     console.log(error);
    //   });
    // },
    // post:function (){
    //   console.log('post请求方法');
    //   //发送post请求
    //   axios.post(('http://127.0.0.1:3000/123'),{id:12},
    //     {'Content-Type':'application/x-www-form-urlencoded'}
    //   ).then((response)=>{
    //     console.log(response.data);
    //   }).catch(function (error) {
    //     console.log(error);
    //   });
    // },
    presentResult(event) {
      console.log(event)
    }
  },
  /**
   * Chart data used to render stats, charts. Should be replaced with server data
   */
  data() {
    return {
      request: {
        type: "time", //time or io
        nodeCount: 27,
        dataset: "Non-IID",
        malicious: 30,
      },
      collaborationChart_21: {
        data: {
          labels: [
            "10",
            "20",
            "30",
            "40",
            "50",
            "60",
          ],
          series: [
            [1.01243114785, 1.1256127735600001, 1.239308446383333, 0.41384830810000006, 0.6262020263499999, 0.8006741681999999],
            [4.70663796552, 2.8865191167, 1.0694188075999997, 1.9813261104000002, 3.7629165652250007, 0],
            [3.475861579075, 4.453691886680001, 5.265801555016667, 1.8381625571500002, 2.6829958631666666, 1.1246912123],
          ]
        },
        options: {
          seriesBarDistance: 10,
          axisX: {
            showGrid: false
          },
          height: "245px"
        }
      },        
      collaborationChart_24: {
        data: {
          labels: [
            "10",
            "20",
            "30",
            "40",
            "50",
            "60",
          ],
          series: [
            [1.008650195225, 1.1903347819399999, 0.6530291177499999, 1.2183475917666662, 0.43438218019999997, 0.7808396103999999],
            [4.321481943250001, 3.3393605189666657, 1.2140650719, 2.36434074805, 0, 0],
            [5.356896238080001, 2.20745090515, 4.11206418675, 3.178620079533333, 1.2626021306, 0],
          ]
        },
        options: {
          seriesBarDistance: 10,
          axisX: {
            showGrid: false
          },
          height: "245px"
        }
      },      
      collaborationChart_27: {
        data: {
          labels: [
            "10",
            "20",
            "30",
            "40",
            "50",
            "60",
          ],
          series: [
            [1.3358427407666666, 0.8459825369333335, 1.2407417205, 0.6164867736, 1.1037270801999999, 0.4280409224],
            [2.6432800331000004, 1.4411526239, 3.7746705084666656, 0, 0, 0],
            [3.6596769165333325, 1.4198744763, 2.6524237169, 0, 0, 0],
          ]
        },
        options: {
          seriesBarDistance: 10,
          axisX: {
            showGrid: false
          },
          height: "245px"
        }
      },
      accuracyChart_10: {
        data: {
          labels: [
            0,
            5,
            10,
            15,
            20,
            25,
            30,
          ],
          series: [
            [0, 90.0, 90.06333333333333, 90.21333333333332, 90.06666666666668, 90.09666666666665, 89.93333333333334],
            [0, 47.25, 41.32666666666666, 46.336666666666666, 41.60333333333333, 36.70666666666667,41.18],
            [0, 78.82, 78.98, 78.23, 78.58666666666666, 78.82000000000001],
          ]
        },
        options: {
          low: 0,
          high: 100,
          seriesBarDistance: 10,
          axisX: {
            showGrid: false
          },
          height: "245px"
        }
      },       
      accuracyChart_20: {
        data: {
          labels: [
            0,
            5,
            10,
            15,
            20,
            25,
            30,
          ],
          series: [
            [0, 90.0, 90.00666666666667, 89.92, 89.86666666666667, 89.64999999999999,89.53000000000002],
            [0, 35.623333333333335, 28.223333333333333, 31.406666666666666, 26.76, 39.303333333333335],
            [0, 73.81, 73.48333333333333, 73.28333333333332, 73.69333333333334, 73.62666666666667, 74.17666666666666],

          ]
        },
        options: {
          low: 0,
          high: 100,
          seriesBarDistance: 10,
          axisX: {
            showGrid: false
          },
          height: "245px"
        }
      },         
      accuracyChart_30: {
        data: {
          labels: [
            0,
            5,
            10,
            15,
            20,
            25,
            30,
          ],
          series: [
            [0, 89.77, 89.79, 89.67999999999999, 89.69333333333334, 89.60333333333334, 89.52],
            [0, 28.153333333333332, 30.093333333333334, 28.64, 29.30666666666667, 23.173333333333336, 27.393333333333334],
            [0, 63.20000000000001, 63.586666666666666, 63.24666666666667, 63.529999999999994, 63.26333333333333, 63.223333333333336],

          ]
        },
        options: {
          low: 0,
          high: 100,
          seriesBarDistance: 10,
          axisX: {
            showGrid: false
          },
          height: "245px"
        }
      },      
    };
  }
};
</script>
<style>
</style>
