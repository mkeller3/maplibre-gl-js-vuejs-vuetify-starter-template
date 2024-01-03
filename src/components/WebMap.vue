<template>
    <div id="map"></div>
</template>

<script setup>
import maplibregl from "maplibre-gl";
import { onMounted } from 'vue';

onMounted(() => {
    const map = new maplibregl.Map({
        container: 'map',
        style: {
            'version': 8,
            'sources': {
                'raster-tiles': {
                    'type': 'raster',
                    'tiles': [
                        'https://tile.openstreetmap.org/{z}/{x}/{y}.png'
                    ],
                    'tileSize': 256,
                    'attribution':
                        'Data &copy; <a href="https://www.openstreetmap.org/about" target="_blank">OpenStreetMap</a> contributors'
                }
            },
            'layers': [
                {
                    'id': 'simple-tiles',
                    'type': 'raster',
                    'source': 'raster-tiles',
                    'minzoom': 0,
                    'maxzoom': 22
                }
            ]
        },
        center: [-95, 40],
        zoom: 4
    })

    map.addControl(new maplibregl.NavigationControl());
    map.addControl(new maplibregl.FullscreenControl());
})
</script>


<style scoped>
#map {
    height: 100vh;
}
</style>