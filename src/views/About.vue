<template>
  <div>
    <i-container>
      <i-row>
        <i-column v-for="song in songs" :key="song.name" xs="4">
          <i-card>
            <img slot="image" :src="song.image[3]['#text']" alt="Card Image" />
            <h4 class="title">{{song.name}}</h4>
            <p class="subtitle">{{song.artist.name}}</p>
            <a class="link" href="https://inkline.io">Example Link</a>
          </i-card>
        </i-column>
      </i-row>
    </i-container>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name:'About',
  data() {
    return {
      songs:[]
    }
  },
  methods: {
    getSongs() {
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
          this.songs = resp.data.tracks.track;
        });
    }
  },
  mounted() {
    this.getSongs()
  }
}
</script>