<template>
  <div class="home">

        <apexchart width="580" type="donut" :options="options" :series="series"></apexchart>
        <button type="button" class="btn btn-primary" @click="logout">Log Out</button>
  </div>
</template>

<script>
// @ is an alias to /src
import { ref , onMounted} from "vue";


export default {
  name: 'ChartView',
  components: {
   
  }, setup() {
        const options = ref({});
        const series = ref([44, 55, 41, 17, 15]);
        const logout = function() {
  localStorage.removeItem('user');
  location.reload()
}
        onMounted(async () => {
          let token = localStorage.getItem("user");

var response = await fetch("/api/bookings/aggregate/groupby", {
    headers: {
      "x-access-token": token
    }
});
});
        return {
            options, series,logout
        }
    },
}
</script>
