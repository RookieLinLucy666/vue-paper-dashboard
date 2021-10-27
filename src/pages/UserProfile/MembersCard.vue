<template>
  <card class="card" :title="title">
    <div>
      <ul class="list-unstyled team-members">
        <li>
          <div class="row" v-for="member in members" :key="member.name">
            <div class="col-3">
              <div class="avatar">
                <img :src="member.image" alt="Circle Image" class="rounded img-fluid">
              </div>
            </div>
            <div class="col-6">
              {{member.name}}
              <br>
              <span :class="getStatusClass(member.status)">
                <small>{{member.status}}</small>
              </span>
            </div>

            <div class="col-31">
              <p-button type="success" outline icon>
                <i class="ti-key"></i>
              </p-button>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </card>
</template>
<script>
export default {
  data() {
    var names = ["e10adc3949ba59","7c4a8d09ca3762a","3ba3253876aed6","969eef6ecad3c29a",
      "f0c3f5d5a86aff3","9cca1ae7594599","a1b7486076a2e11"];
    var statuslist = ["invalid", "success", "failed"];
    // var images = ["@/assets/img/faces/face-1.jpg", "@/assets/img/faces/face-4.png", "@/assets/img/faces/face-5.png"]
    return {
      title: "Cross-domain authenticaiton members",
      members: [
        {
          image: require("@/assets/img/faces/face-1.jpg"),
          name: names[Math.floor(Math.random() * 7)],
          status: statuslist[Math.floor(Math.random() * 3)]
        },
        {
          image: require("@/assets/img/faces/face-4.png"),
          name: names[Math.floor(Math.random() * 7)],
          status: statuslist[Math.floor(Math.random() * 3)]
        },
        {
          image: require("@/assets/img/faces/face-5.png"),
          name: names[Math.floor(Math.random() * 7)],
          status: statuslist[Math.floor(Math.random() * 3)]
        }
      ]
    };
  },
  created(){
    setInterval(this.scroll,2000)
  },
  methods: {
    getStatusClass(status) {
      switch (status) {
        case "invalid":
          return "text-muted";
        case "success":
          return "text-success";
        case "failed":
          return "text-danger";
        default:
          return "text-success";
      }
    },
    scroll(){
      this.animate=true;    // 因为在消息向上滚动的时候需要添加css3过渡动画，所以这里需要设置true
      setTimeout(()=>{      //  这里直接使用了es6的箭头函数，省去了处理this指向偏移问题，代码也比之前简化了很多
        this.members.push(this.members[0]);  // 将数组的第一个元素添加到数组的
        this.members.shift();               //删除数组的第一个元素
        this.animate=false;  // margin-top 为0 的时候取消过渡动画，实现无缝滚动
      },1000)
    }
  }
};
</script>
<style>
</style>
