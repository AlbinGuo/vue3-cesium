<script setup>
  import { onMounted } from 'vue'
  import * as Cesium from 'cesium';

  onMounted(() => {
    const custom = new Cesium.ArcGisMapServerImageryProvider({
      url: '//services.arcgisonline.com/ArcGIS/rest/services/World_Street_Map/MapServer',
    })

    const viewer = new Cesium.Viewer('cesiumContainer', {
      // 地球样式widget显示与隐藏 - 左上角
      baseLayerPicker : true,
      imageryProvider: custom,
      terrainProvider: Cesium.createWorldTerrain({
         requestVertexNormals: false,
          requestWaterMask: true
      }),
      // 全屏显示按钮
      fullscreenButton: false,
      // VR按钮是否显示  -右下角
      vrButton: true,
      // 是否显示下方文字描述【This application is using...】
      geocoder: false,
      // 是否显示home按钮 - 右上角
      homeButton: true,
      timeline: false
    }); 
  })
</script>

<template>
  <div id="cesiumContainer"></div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
html,
body,
#cesiumContainer {
  width: 100%;
  height: 100%;
  margin: 0;
  padding: 0;
  overflow: hidden;
}
</style>
