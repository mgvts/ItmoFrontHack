<template>
  <div class="root">
    <ActivityPage v-for="activity in activities" :activity="activity" :key="activity.id"/>
    <GraphActivity :activity-info="null"/>
  </div>
</template>

<script>

import ActivityPage from "@/components/pages/ActivityPageEasy.vue";
import GraphActivity from "@/components/pages/GraphActivity.vue";
import axios from "core-js/internals/queue";

export default {
  name: 'App',
  components: {
    GraphActivity,
    ActivityPage,
  },

  data: function () {
    return {
      activitiesSortedByName: [],
      activities: [],
    }
  },

  beforeMount() {
    axios.get("http://127.0.0.1:5000/allData").then(response => {
        console.log(response)
      this.activities = response.data;
    });
    // sorting it by name...

  }
}
</script>
