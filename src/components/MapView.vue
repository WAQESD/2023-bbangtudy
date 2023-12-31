<script setup>
import { ref, onMounted } from "vue";

const script = document.createElement("script");
const map = ref(null);
const colors = [];

function generatePastelColors(n) {
  for (var i = 0; i < n; i++) {
    // Hue (note 0 and 360 are the same and represent red, 120 represents green and 240 represents blue)
    var h = Math.floor((360 * i) / n);
    // Saturation
    var s = 100;
    // Lightness
    var l = 85; // You can adjust the lightness value to get the pastel effect
    colors.push("hsl(" + h + "," + s + "%," + l + "%)");
  }
  return colors;
}

const cafeInfos = [
  { title: "꾸드뱅", date: "2023.08.20", lat: 36.3867659, lng: 127.3087717 },
  { title: "데코르", date: "2023.08.27", lat: 36.3835046, lng: 127.3204775 },
  { title: "에이트", date: "2023.09.03", lat: 36.3598589, lng: 127.3498251 },
  { title: "블레스롤", date: "2023.09.10", lat: 36.3590397, lng: 127.3535707 },
  { title: "글로리데이즈", date: "2023.09.17", lat: 36.3613382, lng: 127.3481366 },
  { title: "캘리포니아 베이커리&카페", date: "2023.09.24", lat: 36.3496956, lng: 127.387414 },
  { title: "소올투베이커리", date: "2023.09.28", lat: 36.3523648, lng: 127.3768559 },
  { title: "탐앤탐스", date: "2023.10.03", lat: 36.3530713, lng: 127.3450705 },
  { title: "폴바셋", date: "2023.10.09", lat: 36.3751116, lng: 127.382032 },
  { title: "하레하레", date: "2023.10.15", lat: 36.3068472, lng: 127.3490893 },
  { title: "탐앤탐스", date: "2023.10.22", lat: 36.3530713, lng: 127.3455705 },
  { title: "2023 대전 빵축제", date: "2023.10.28", lat: 36.3215267, lng: 127.4111425 },
  { title: "탐앤탐스", date: "2023.10.29", lat: 36.3530713, lng: 127.3460705 },
  { title: "하이테이블", date: "2023.11.05", lat: 36.3545985, lng: 127.3432228 },
  { title: "탐앤탐스", date: "2023.11.12", lat: 36.3530713, lng: 127.3465705 },
  { title: "홀리크로스", date: "2023.11.19", lat: 36.3521368, lng: 127.3769057 },
  { title: "하늘만큼", date: "2023.12.13", lat: 36.3204879, lng: 127.4561457 },
  { title: "꾸드뱅", date: "2023.12.14", lat: 36.3867659, lng: 127.3092717 },
  { title: "남선공원 스케이트장", date: "2023.12.18", lat: 36.3452575, lng: 127.3966837 },
  { title: "신세계 백화점 스포츠 몬스터", date: "2023.12.19", lat: 36.3751116, lng: 127.383032 },
  { title: "공간태리", date: "2023.12.25", lat: 36.3454756, lng: 127.29348 },
  { title: "에이트", date: "2023.12.26", lat: 36.3598589, lng: 127.3503251 },
  { title: "읍천리382", date: "2023.12.28", lat: 36.3534601, lng: 127.3406304 },
];

generatePastelColors(cafeInfos.length);

onMounted(() => {
  script.type = "text/javascript";
  script.src = `https://oapi.map.naver.com/openapi/v3/maps.js?ncpClientId=${import.meta.env.VITE_MAP_API_KEY}`;

  document.querySelector("head").appendChild(script);

  script.addEventListener("load", () => {
    map.value = new window.naver.maps.Map("map", {
      center: new window.naver.maps.LatLng(import.meta.env.VITE_MAP_LAT, import.meta.env.VITE_MAP_LNG),
      zoom: 11,
    });

    cafeInfos.forEach((cafe, idx) => {
      let marker = new window.naver.maps.Marker({
        position: new window.naver.maps.LatLng(cafe.lat, cafe.lng),
        map: map.value,
        icon: {
          content:
            `<div style='display:flex; flex-direction:column; box-sizing: border-box; border-radius:16px; width:32px; height:32px; background-color:${colors[idx]}'> ` +
            `<h5 style='color:black; line-height:32px; text-align: center;'>${idx + 1}</h5>` +
            "</div>",
          size: new window.naver.maps.Size(32, 32),
          anchor: new window.naver.maps.Point(16, 16),
        },
      });

      var contentString =
        "<div style='display:flex; flex-direction:column; padding: 12px; text-align: center'> " +
        `<h1 style='color:black; font-family: "ONE-Mobile-POP" !important;'>${cafe.title}</h1>` +
        `<h4 style='color:black; font-family: "ONE-Mobile-POP" !important;'>${cafe.date}</h4>` +
        "</div>";

      var infowindow = new window.naver.maps.InfoWindow({
        content: contentString,
      });

      window.naver.maps.Event.addListener(marker, "click", function () {
        if (infowindow.getMap()) {
          infowindow.close();
        } else {
          infowindow.open(map.value, marker);
        }
      });
    });
  });
});
</script>

<template>
  <div class="map-container">
    <h1 class="map-title">🥯 지도로 보는 빵터디 🥯</h1>
    <div id="map"></div>
  </div>
</template>

<style scoped>
.map-container {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
}

h1 {
  padding: 10px;
  font-size: 32px;
  font-family: "seolleimcool-SemiBold" !important;
  margin-bottom: 30px;
  text-align: center;
}

#map {
  width: 94%;
  aspect-ratio: 1/1;
  margin-bottom: 24px;
}
</style>
