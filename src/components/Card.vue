
<template>
<div class="background">
  <div class="card-margin p-3">
    <h3>Ready for flights</h3>
    <hr />
    <!-- card header start-->
    <div class="card-header m-2 p-2">
      <b-card body-class="text-center" header-tag="nav">
        <template #header> </template>
      </b-card>
    </div>
    <!-- card header end -->

    <!-- card header start-->
    <div class="cards">
      <h6>Flights</h6>
      <hr />
      <b-card-group class="card-group p-8 m-5">
        <b-card title="Leaving From " id="card1">
          <b-card-text>
            <div>
              <b-form-input
                v-model="searchfrom1"  @input="searchfrom()"
                placeholder="Enter your name"
              ></b-form-input>
              <div class="mt-2">Value: {{ searchfrom1 }}</div>
            </div>
          </b-card-text>
        </b-card>

 <p id="fromcity"></p>
            <div
              class="from-list"
              v-if="status_flight_from"
              style="position: absolute; z-index: 1000"
                id="flightfrom-code-list"
            >
              <table>
                <tr
                  v-for="(flight, index) in flight_code_from"
                  :key="index"
                  style="cursor: pointer; background-color: whitesmoke"
                >
                  <td scope="col" @click="setFlightFrom(flight)">
                    <b> {{ flight[1] }}</b> ,<b>{{ flight[2] }}</b> ,
                    {{ flight[0] }}
                  </td>
                </tr>
              </table>
            </div>
        <b-card title="GoingTo" id="card2">
          <b-card-text>
            <div>
              <b-form-input
                v-model="searchfrom2"
                placeholder="Enter your name"
              ></b-form-input>
              <div class="mt-2">Value: {{ searchfrom2}}</div>
            </div>
          </b-card-text>
        </b-card>
          <p id="tocity"></p>
            <div
              class="from-list"
              v-if="status_flight_to"
              style="position: absolute; z-index: 1000"
              id="flightto-code-list"
            >
              <tr
                v-for="(flight, index) in flight_code_to"
                :key="index"
                style="cursor: pointer; background-color: whitesmoke"
              >
                <td scope="col" @click="setFlightTo(flight)">
                  <b> {{ flight[1] }}</b> ,<b>{{ flight[2] }}</b> ,
                  {{ flight[0] }}
                </td>
              </tr>
            </div>

        <b-card id="card3">
          <div class="col d-box text-center">


            <span class="text-muted"> Departing On </span>

            <div>
              <label for="example-datepicker1">Choose a date</label>
              <b-form-datepicker
                id="example-datepicker1"
                v-model="departureDate"
                class="mb-2"
              ></b-form-datepicker>
              <p>Value: '{{ departureDate }}'</p>
            </div>

            <hr class="my-4" />

            <span class="text-muted"> Returning On </span>

            <div>
              <label for="example-datepicker">Choose a date</label>
              <b-form-datepicker
                id="example-datepicker"
                v-model="arrivalDate"
                class="mb-2"
              ></b-form-datepicker>
            </div>
            <div class="mt-2">Value: {{ arrivalDate }}</div>
          </div>
        </b-card>

        <b-card title="Search" id="card4">
          <b-card-text>
            <div>
              <b-form-input
                v-model="search"
                placeholder="Search"
              ></b-form-input>
              <div class="mt-2">Value: {{ search }}</div>
            </div>
          </b-card-text>
        </b-card>

        <b-card id="card5">

            <a href="https://ibb.co/V9FPgvp"
              ><img
                src="https://i.ibb.co/kBLW4h6/pascal-meier-UYies-SO4-Fi-M-unsplash.jpg"
                alt="pascal-meier-UYies-SO4-Fi-M-unsplash"
                border="0" height="400px" width="600px"
            /></a>

        </b-card>
      </b-card-group>
    </div>
    <!-- card end -->
  </div>
  </div>
</template>


<script>
import { autocomplete } from "air-port-codes-node";
export default {
  name: "Card",

  data() {
    return {
      status_flight_from:null,
      status_flight_to: null,
      leavingFrom: "",

      search:" ",
      searchfrom1:null,
      searchfrom2:null,

      arrivalDate:" ",
      departureDate:" ",

       flight_list: [],
       flight_code_from: [],
      flight_code_to: [],


apca: autocomplete({
        key: "5f2eb93f3d",
        secret: "b4720e474d1ad09", // Your API Secret Key: use this if you are not connecting from a web server
        limit: 15,
      }),
       };
  },


       methods: {
       searchfrom() {
     this.status_flight_from = true;
      this.apca.request(this.from);
      // SUCCESS we found some airports
      this.apca.onSuccess = (data) => {
        if (data.airports.length > 0 && this.from.length > 0) {
          document.getElementById("flightfrom-code-list").style.display =
            "block";
          this.flight_code_from = [];
          for (let i = 0; i < data.airports.length; i++) {
            this.flight_code_from[i] = [
              data.airports[i].name,
              data.airports[i].city,
              data.airports[i].iata,
            ];
          }
        }
      };
      // FAIL no airports found
      this.apca.onError = (data) => {
        console.log("onError", data.message);
      };
    },
    searchto() {
      this.status_flight_to = true;
      this.apca.request(this.to);
      // SUCCESS we found some airports
      this.apca.onSuccess = (data) => {
        if (data.airports.length > 0 && this.to.length > 0) {
          document.getElementById("flightto-code-list").style.display = "block";
          this.flight_code_to = [];
          for (let i = 0; i < data.airports.length; i++) {
            this.flight_code_to[i] = [
              data.airports[i].name,
              data.airports[i].city,
              data.airports[i].iata,
            ];
          }
        }
      };
      // FAIL no airports found
      this.apca.onError = (data) => {
        console.log("onError", data.message);
      };
    },
     setFlightFrom(flight) {
      this.from = flight[2];
      document.getElementById("flightfrom-code-list").style.display = "none";
      document.getElementById(
        "fromcity"
      ).innerHTML = `${flight[0]}<br><b>${flight[1]}</b>`;
    },
    setFlightTo(flight) {
      this.to = flight[2];
      this.destination = flight[1];
      document.getElementById("flightto-code-list").style.display = "none";
      document.getElementById(
        "tocity"
      ).innerHTML = `${flight[0]}<br><b>${flight[1]}</b>`;
    },



    greet(event) {
      // `this` inside methods points to the current active instance
      alert("Hello " + this.name + "!");
      // `event` is the native DOM event
      if (event) {
        alert(event.target.tagName);
      }
    },
  },
};
</script>


<style scoped >
.cards {
  margin-top: 200px;
  height: 0px;
  width: 1400px;
  margin: 2px;
  padding: 3px;
}
/* #card1{
width: 8px;
  height: 10px;
} */

.card-margin {
  border: 3px solid teal;
  margin: 10px;
  height: 80vh;
}

#card1,
#card2,
#card3,
#card4 {
  height: 360px;
  width: 100px;
  /* background-color: blueviolet; */
 background-image: linear-gradient(to bottom, #33ccff 0%, #ff99cc 100%);
}

.card-group {
  height: 500px;
  width: 1300px;
  background-color: beige;
}

#card5 {
  height: 360px;
  width: 100px;
  border-color: rgb(241, 253, 253);
}

/* #photo {
  width: 500px;
  height: 200px;
  padding:0%;
  margin: 0%;
} */


.background
{
  background-image: linear-gradient(to bottom, #33ccff 0%, #ff99cc 100%);
}
</style>


