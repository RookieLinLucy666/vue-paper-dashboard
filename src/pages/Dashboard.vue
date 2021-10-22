<template>
  <div>

    <!--Stats cards-->
    <div class="row">
      <div class="col-md-6 col-xl-3" v-for="stats in statsCards" :key="stats.title">
        <stats-card>
          <div class="icon-big text-center" :class="`icon-${stats.type}`" slot="header">
            <i :class="stats.icon"></i>
          </div>
          <div class="numbers" slot="content">
            <p>{{stats.title}}</p>
            {{stats.value}}
          </div>
          <div class="stats" slot="footer">
            <i :class="stats.footerIcon"></i> {{stats.footerText}}
          </div>
        </stats-card>
      </div>
    </div>

    <!--Charts-->
    <div class="row">

      <div class="col-12">
        <chart-card title="Operation Analysis"
                    sub-title="24 Hours performance"
                    :chart-data="usersChart.data"
                    :chart-options="usersChart.options">
          <span slot="footer">
            <i class="ti-reload"></i> Updated Now  
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Identity Authentication
            <i class="fa fa-circle text-danger"></i> Data Collaboration
            <i class="fa fa-circle text-warning"></i> Computing Collaboration
          </div>
        </chart-card>
      </div>

<!--       <div class="col-md-6 col-12">
        <chart-card title="Email Statistics"
                    sub-title="Last campaign performance"
                    :chart-data="preferencesChart.data"
                    chart-type="Pie">
          <span slot="footer">
            <i class="ti-timer"></i> Campaign set 2 days ago</span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Open
            <i class="fa fa-circle text-danger"></i> Bounce
            <i class="fa fa-circle text-warning"></i> Unsubscribe
          </div>
        </chart-card>
      </div> -->

      <div class="col-md-6 col-12">
        <chart-card title="Collaboration Performance"
                    sub-title="Collaboration time when node=27"
                    :chart-data="collaborationChart.data"
                    :chart-options="collaborationChart.options">
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

      <div class="col-md-6 col-12">
        <chart-card title="Accuracy Performance"
                    sub-title="Accuracy in Non-IID FMNIST dataset when malicious=30%"
                    :chart-data="accuracyChart.data"
                    :chart-options="accuracyChart.options">
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
    get:function(){
      console.log('get请求方法');
      //发送get请求
      axios.get('http://127.0.0.1:3000/123')
        .then(reponse=>{
          console.log(reponse.data)
        }).catch(function (error) {
        console.log(error);
      });
    },
    post:function (){
      console.log('post请求方法');
      //发送post请求
      axios.post(('http://127.0.0.1:3000/123'),{id:12},
        {'Content-Type':'application/x-www-form-urlencoded'}
      ).then((response)=>{
        console.log(response.data);
      }).catch(function (error) {
        console.log(error);
      });
    }
  },
  /**
   * Chart data used to render stats, charts. Should be replaced with server data
   */
  data() {
    return {
      statsCards: [
        {
          type: "warning",
          icon: "ti-server",
          title: "Block Height",
          value: "44",
          footerText: "Updated now",
          footerIcon: "ti-reload"
        },
        {
          type: "success",
          icon: "ti-wallet",
          title: "Sequence",
          value: "1",
          footerText: "Updated now",
          footerIcon: "ti-reload"
        },
        {
          type: "danger",
          icon: "ti-pulse",
          title: "Transactions",
          value: "23",
          footerText: "Updated now",
          footerIcon: "ti-reload"
        },
        {
          type: "info",
          icon: "ti-user",
          title: "Users",
          value: "+45",
          footerText: "Updated now",
          footerIcon: "ti-reload"
        }
      ],
      usersChart: {
        data: {
          labels: [
            "0:00AM",
            "2:00AM",
            "4:00AM",
            "6:00AM",
            "8:00AM",
            "10:00AM",
            "12:00AM",
            "14:00PM",
            "16:00PM",
            "18:00PM",
            "20:00PM",
            "22:00PM",
          ],
          series: [
            [87, 85, 90, 62, 94, 26, 98, 95, 52, 36, 78, 99],
            [7, 52, 93, 40, 87, 35, 35, 42, 44, 15, 68, 45],
            [3, 13, 7, 8, 90, 39, 7, 10, 10, 30, 25, 33]
          ]
        },
        options: {
          low: 0,
          high: 100,
          showArea: true,
          height: "245px",
          axisX: {
            showGrid: false
          },
          lineSmooth: Chartist.Interpolation.simple({
            divisor: 3
          }),
          showLine: true,
          showPoint: false
        }
      },
      collaborationChart: {
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
            // [0.9767736318499999, 1.6764882840750002, 4.1797204278999995, 1.300403052766667, 1.9640842885999996, 1.90675293108],
            // [4.785351687050001, 2.4549934617, 0, 0, 0, 0],
            // [8.411504395300003, 6.394124279966666, 4.6033623205000005, 2.3863325759, 0, 0],
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
      accuracyChart: {
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
      // preferencesChart: {
      //   data: {
      //     labels: ["62%", "32%", "6%"],
      //     series: [62, 32, 6]
      //   },
      //   options: {}
      // }
    };
  }
};
</script>
<style>
</style>
