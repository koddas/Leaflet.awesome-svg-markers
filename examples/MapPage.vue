<template>
  <ion-page>
    <ion-content :fullscreen="true">
        <div id="container">
          <div id="mapContainer"></div>
        </div>
    </ion-content>
  </ion-page>
</template>

<script lang="javascript">
import { defineComponent } from 'vue';
import { IonPage, IonContent } from '@ionic/vue';
import {
  accessibility
} from 'ionicons/icons';
import L from "leaflet";
import "leaflet/dist/leaflet.css";
import "leaflet.awesome-svg-markers/dist/leaflet.awesome-svg-markers.css";
import "leaflet.awesome-svg-markers";

// Webpack fixes to Leaflet
delete L.Icon.Default.prototype._getIconUrl;
L.Icon.Default.mergeOptions({
  iconRetinaUrl: require('leaflet/dist/images/marker-icon-2x.png'),
  iconUrl: require('leaflet/dist/images/marker-icon.png'),
  shadowUrl: require('leaflet/dist/images/marker-shadow.png'),
});

export default  defineComponent({
  name: 'MapPage',
  components: { IonContent, IonPage },
  data() {
    return {
      map: null
    };
  },
  mounted() {
    this.map = L.map("mapContainer", { zoomControl: false})
      .setView([55.6, 13], 15);
    L.tileLayer("http://{s}.tile.osm.org/{z}/{x}/{y}.png", {
      attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',
    }).addTo(this.map);
    //use a mix of renderers
    var customPane = this.map.createPane("customPane");
    customPane.style.zIndex = 399; // put just behind the standard overlay pane which is at 400
    window.dispatchEvent(new Event('resize'));
    L.marker(
      [55.6, 13],
      {icon: L.AwesomeMarkers.icon({
        svgIcon: accessibility,
        markerColor: 'green',
        iconColor: '#ccc'
      })}).addTo(this.map);
  },
  onBeforeUnmount() {
    if (this.map) {
      this.map.remove();
    }
  },
});
</script>

<style scoped>
#container {
  text-align: center;
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#mapContainer {
  width: 100vw;
  height: 100vh;
}
</style>
