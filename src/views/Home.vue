<template>
  <div>
    <i-container>
      <h1 class="_text-center">Music World</h1>
      <p class="_text-center">
        <img src="../assets/logo.png" alt="Logo" />
      </p>
    </i-container>
    <i-container>
      <h2>Top Songs</h2>
      <i-table striped>
        <thead>
          <tr>
            <th>Artist</th>
            <th>Song</th>
            <th>Listeners</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(track, index) in top_tracks" :key="index">
            <td>{{track.artist.name}}</td>
            <td>{{track.name}}</td>
            <td>{{track.listeners}}</td>
          </tr>
        </tbody>
      </i-table>
    </i-container>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      top_tracks: [],
    };
  },
  methods: {
    getTopSongs() {
      var apiKey = "1af9e86e97666e3818e36bb5fb3c69f0";
      axios
        .get("http://ws.audioscrobbler.com/2.0/", {
          params: {
            api_key: apiKey,
            method: "chart.gettoptracks",
            format: "json"
          }
        })
        .then(resp => {
          console.log(resp.data.tracks.track);
          this.top_tracks = resp.data.tracks.track;
        });
    }
  },
  mounted() {
    this.getTopSongs();
  }
};
</script>