<template>
  <card title="Notifications" sub-title="This is all notifications">
    <div>
      <div class="row">
        <div class="col-md-6">
          <h5>Notifications List</h5>

          <div v-for="notification in notifications" :key="notification.id">
            <div class="alert alert-with-icon" v-bind:class="notification.type" data-notify="container">
              <button type="button" aria-hidden="true" class="close">.</button>
              <span data-notify="icon" class="ti-bell"></span>
              <span data-notify="message">{{notification.title}}</span>
              <span data-notify="message">{{notification.content}}</span>
            </div>
          </div>

        </div>

        <div class="col-md-6">
          <h5>Notification classification</h5>
          <div class="alert alert-info">
            <span>
              <b> Identity Authentication Notification </b> </span>
          </div>
          <div class="alert alert-success">
            <span>
              <b> intra-domain collaborative Notification </b> </span>
          </div>
          <div class="alert alert-warning">
            <span>
              <b> Cross-domain collaborative Notification </b> </span>
          </div>
          <div class="alert alert-danger">
            <span>
              <b> Computing tasks Notification</b> </span>
          </div>
        </div>

      </div>

      <br>
      <br>

    </div>
  </card>
</template>
<script>
import NotificationTemplate from './Notifications/NotificationTemplate';

export default {
  data() {
    var types = ["alert-info", "alert-success", "alert-warning", "alert-danger"];
    return {
      notifications: [
        {
          id: 1,
          title: "notification1",
          type: types[Math.floor(Math.random() * 4)],
          content: "One Identity Authentication Notification has completed."
        },
        {
          id: 2,
          title: "notification2",
          type: types[Math.floor(Math.random() * 4)],
          content: "One Identity Authentication Notification has completed."
        },
        {
          id: 3,
          title: "notification3",
          type: types[Math.floor(Math.random() * 4)],
          content: "One Identity Authentication Notification has completed."
        },
        {
          id: 4,
          title: "notification4",
          type: types[Math.floor(Math.random() * 4)],
          content: "One Cross-domain collaborative Notification has completed."
        },
        {
          id: 5,
          title: "notification5",
          type: types[Math.floor(Math.random() * 4)],
          content: "One Identity Authentication Notification has completed."
        },
      ]
    };
  },
  methods: {
    notifyVue(verticalAlign, horizontalAlign) {
      const color = Math.floor(Math.random() * 4 + 1);
      this.$notify({
        component: NotificationTemplate,
        icon: "ti-gift",
        horizontalAlign: horizontalAlign,
        verticalAlign: verticalAlign,
        // type: types[color]
      });
    }
  }
};
</script>
<style>
</style>
