<script lang="ts">
import { defineComponent } from 'vue';
import FooterSection from './components/FooterSection.vue';
import RatingForm from './components/RatingForm.vue';
import ThankYou from './components/ThankYou.vue';

type RatingType = '1' | '2' | '3' | '4' | '5';

export default defineComponent({
	data() {
		return {
			selected_rating: null as RatingType | null,
		};
	},
	mounted() {
		this.selected_rating = null;
	},
	methods: {
		updateRating(rating: RatingType) {
			this.selected_rating = rating;
		},
	},
	components: {
		FooterSection,
		RatingForm,
		ThankYou,
	},
});
</script>

<template>
	<main>
		<rating-form v-if="!selected_rating" :choose-rating="updateRating" />
		<thank-you v-else :selected_rating="selected_rating" />
	</main>

	<footer-section />
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Overpass:wght@400;700&display=swap');
@import './assets/scss/base.scss';
@import './assets/scss/variables.scss';

#app {
	min-height: 100%;
	font-family: 'Overpass', sans-serif;
	font-size: 15px;
	background-color: $Very-Dark-Blue;
	display: grid;
	place-items: center;

	main {
		width: 375px;
		max-width: 90%;
		height: 375px;
		border-radius: 28px;
		background-color: $Dark-Blue;
	}
}
</style>
