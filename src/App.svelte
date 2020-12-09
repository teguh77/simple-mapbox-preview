<script>
	import {onMount} from 'svelte'
	import mapboxgl from 'mapbox-gl'
	import "mapbox-gl/dist/mapbox-gl.css"

	import Directions from '@mapbox/mapbox-gl-directions/dist/mapbox-gl-directions'
	import "@mapbox/mapbox-gl-directions/dist/mapbox-gl-directions.css"
	mapboxgl.accessToken = 'pk.eyJ1IjoidGVndWg3IiwiYSI6ImNrMmd3N2NpajAwb2YzbG9ia3BlMzdjZ2IifQ.2GXhXwD6vHGeDXWmWfiR-w';

	let container;




	function setupMap() {
		const map = new mapboxgl.Map({
		  container,
		  style: 'mapbox://styles/mapbox/streets-v11',
		  zoom: 2
		});

		map.addControl(new mapboxgl.NavigationControl())

		const directions = new Directions({
			accessToken: mapboxgl.accessToken,
			unit: 'metric',
			profile: 'mapbox/cycling'
		})

		map.addControl(directions, 'top-left');

	}

	onMount(setupMap)
</script>

<div id="map" bind:this={container}></div>

<style>
	#map {
		height: 100vh;
		width: 100%;
	}
</style>
