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
        <chart-card title="Data Analysis"
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

      <div class="col-md-6 col-12">
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
      </div>

      <div class="col-md-6 col-12">
        <chart-card title="2015 Sales"
                    sub-title="All products including Taxes"
                    :chart-data="activityChart.data"
                    :chart-options="activityChart.options">
          <span slot="footer">
            <i class="ti-check"></i> Data information certified
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> Tesla Model S
            <i class="fa fa-circle text-warning"></i> BMW 5 Series
          </div>
        </chart-card>
      </div>

    </div>

  </div>
</template>
<script>
import { StatsCard, ChartCard } from "@/components/index";
import Chartist from 'chartist';
export default {
  components: {
    StatsCard,
    ChartCard
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
      activityChart: {
        data: {
          labels: [
            "Jan",
            "Feb",
            "Mar",
            "Apr",
            "Mai",
            "Jun",
            "Jul",
            "Aug",
            "Sep",
            "Oct",
            "Nov",
            "Dec"
          ],
          series: [
            [542, 543, 520, 680, 653, 753, 326, 434, 568, 610, 756, 895],
            [230, 293, 380, 480, 503, 553, 600, 664, 698, 710, 736, 795]
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
      preferencesChart: {
        data: {
          labels: ["62%", "32%", "6%"],
          series: [62, 32, 6]
        },
        options: {}
      }
    };
  }
};
</script>
<style>
</style>
