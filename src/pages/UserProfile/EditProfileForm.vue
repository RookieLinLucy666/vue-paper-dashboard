<template>
<!--  <card class="card" title="Performance Analysis">-->
    <div>
      <div class="col-12">
        <chart-card title="Average Concurrent Query Time"
                    sub-title="In Multiple Domains"
                    :chart-data="activityChart.data"
                    :chart-options="activityChart.options">
          <span slot="footer">
            <i class="ti-timer"></i> test in experimental environment
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> 4 domain with 50 certificates
            <i class="fa fa-circle text-warning"></i> 4 domain with 100 certificates
            <i class="fa fa-circle text-danger"></i> 8 domain with 50 certificates
            <i class="fa fa-circle text-success"></i> 8 domain with 100 certificates
          </div>
        </chart-card>
      </div>
    </div>
<!--  </card>-->
</template>
<script>
import { StatsCard, ChartCard } from "@/components/index";

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
      activityChart: {
        data: {
          labels: [
            "50",
            "100",
            "150",
            "200",
            "250",
            "300",
            "350",
            "400"
          ],
          series: [
            [7, 6.7, 7, 6.5, 6.6, 6.5, 6.9, 6.5],
            [7.1, 6.2, 6.6, 6.3, 6.3, 6.6, 6.7, 6.9],
            [7, 6.5, 6.8, 6.15, 6.6, 6.8, 6.8, 6.8],
            [7.4, 6.6, 6.9, 6.8, 6.8, 6.8, 6.8, 6.9]
          ]
        },
        options: {
          seriesBarDistance: 10,
          axisX: {
            showGrid: false
          },
          height: "245px"
        }
      }
    };
  }
};
</script>
<style>
</style>
