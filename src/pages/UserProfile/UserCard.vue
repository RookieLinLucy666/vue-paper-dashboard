<template>
  <card class="card-user">
    <div>
      <div class="col-12">
        <chart-card title="Distributed Ledger Content"
                    sub-title="Field Size"
                    :chart-data="preferencesChart.data"
                    chart-type="Pie">
          <span slot="footer">
            <i class="ti-check"></i> Data information certified
          </span>
          <div slot="legend">
            <i class="fa fa-circle text-info"></i> certId
            <i class="fa fa-circle text-warning"></i> Hash
            <i class="fa fa-circle text-danger"></i> CA
            <i class="fa fa-circle text-success"></i> Status
          </div>
        </chart-card>
      </div>
    </div>
  </card>
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
      preferencesChart: {
        data: {
          labels: ["16%", "64%", "16%", "4%"],
          series: [16, 64, 16, 4]
        },
        options: {}
      }
    };
  }
};
</script>
<style>
</style>
