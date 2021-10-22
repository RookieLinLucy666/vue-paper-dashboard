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
export default {

  methods: {
    addRequest(event) {
      console.log("aaaa")
    }
  }

};
</script>
<style>
</style>
