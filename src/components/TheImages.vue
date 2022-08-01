<template>
	<h1 class="title">Random Image Feed</h1>
	<div class="container">
		<img v-for="image in images" :key="image.url" :src="image.url" alt="" />
	</div>
</template>

<script>
export default {
	data() {
		return {
			unsplashUrl: 'https://source.unsplash.com/random/',
			rows: 10,
			images: [],
		}
	},
	computed: {},
	methods: {
		getRandomNr() {
			return Math.floor(Math.random() * 10) + 300
		},
		getRandomSize() {
			return `${this.getRandomNr()}x${this.getRandomNr()}`
		},
		addImages() {
			for (let i = 0; i < this.rows * 3; i++) {
				let imageObject = {}
				imageObject.url = this.unsplashUrl + this.getRandomSize()
				this.images.push(imageObject)
			}
		},
	},
	created() {
		this.addImages()
	},
}
</script>
