<template>
  <div></div>
</template>

<script>
import Vue from "vue";
import axios from "axios";

Vue.use(axios);

export default {
  mounted() {
    axios
      .get(
        "https://api.sharetrip.net/api/v1/flight/search?tripType=Return&adult=1&child=0&infant=0&class=Economy&origin=DAC&destination=DXB&depart=2021-12-25&depart=2021-12-30"
      )
      .then((response) => {
        // response = JSON.stringify(response);

       let Flights = [];
        //response = JSON.parse(response);
        //console.log(originalCity);
        const originalCity =
          response.data.response.flights[0].flight[0].originName.city;
          const originalAirport=
        response.data.response.flights[0].flight[0].originName.airport;
        const destinationCity =
        response.data.response.flights[0].flight[0].destinationName.city;
          const destinationAirport=
         response.data.response.flights[0].flight[0].destinationName.airport;
        const departureTime =
      response.data.response.flights[0].flight[0].departureDateTime.date;
        const arrivalTime =
        response.data.response.flights[0].flight[0].arrivalDateTime.date;



       const flightData =
       {
             originalCity:originalCity,
             originalAirport:originalAirport,
             destinationCity:destinationCity,
             destinationAirport:destinationAirport,
             departureTime:departureTime,
             arrivalTime:arrivalTime

       }

        Flights.push(flightData)

        console.log(flightData);




      });
  },

  /* data () {
    return {
      info:
    }
} */



};
</script>


