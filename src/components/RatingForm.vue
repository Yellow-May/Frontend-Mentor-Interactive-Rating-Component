<script lang="ts">
import { defineComponent } from 'vue';
import type { PropType } from 'vue';

type RatingType = '1' | '2' | '3' | '4' | '5';
const formGroups: RatingType[] = ['1', '2', '3', '4', '5'];

export default defineComponent({
	data() {
		return {
			rating_pick: '1' as RatingType,
			formGroups,
		};
	},
	mounted() {
		this.rating_pick = '1';
	},
	props: {
		chooseRating: {
			type: Function as PropType<(rating: RatingType) => void>,
			required: true,
		},
	},
	methods: {
		onsubmit(e: Event) {
			e.preventDefault();
			this.chooseRating(this.rating_pick);
		},
	},
});
</script>

<template>
	<section class="rating">
		<div class="logo">
			<img src="../assets/images/icon-star.svg" alt="star" />
		</div>

		<div class="intro">
			<h1>How did we do?</h1>

			<p>
				Please let us know how we did with your support request. All feedback is appreciated to help us improve our offering!
			</p>
		</div>

		<form name="select-rating" class="select-rating" @submit="onsubmit">
			<fieldset>
				<div v-for="formGroup in formGroups" :key="formGroup" class="form-group">
					<input type="radio" name="rating" :id="formGroup" :value="formGroup" v-model="rating_pick" />
					<label :for="formGroup">{{ formGroup }}</label>
				</div>
			</fieldset>

			<button type="submit" title="submit review">Submit</button>
		</form>
	</section>
</template>

<style lang="scss" scoped>
@import '../assets/scss/variables.scss';

.rating {
	height: 100%;
	padding: 28px;
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	gap: 24px;

	.logo {
		width: 40px;
		height: 40px;
		border-radius: 50%;
		background: rgba($Medium-Grey, 0.1);
		display: grid;
		place-items: center;

		img {
			width: 33.33%;
		}
	}

	.intro {
		h1 {
			color: $White;
			font-size: 1.65em;
			font-weight: 700;
			margin-bottom: 0.5rem;
		}

		p {
			line-height: 1.6;
			color: $Light-Grey;
			font-size: 1em;
		}
	}

	form.select-rating {
		display: grid;
		gap: 24px;

		fieldset {
			border: none;
			display: flex;
			justify-content: space-between;
			align-items: center;
			padding: 0;

			div.form-group {
				width: 45px;
				height: 45px;
				border-radius: 50%;
				position: relative;
				display: grid;
				place-items: center;

				label {
					color: $Medium-Grey;
					font-size: 1em;
					font-weight: 700;
					width: 100%;
					height: 100%;
					border-radius: 50%;
					display: grid;
					place-items: center;
					background: rgba($Medium-Grey, 0.1);
					transition: 0.2s ease-in-out;
					cursor: pointer;
				}

				input {
					position: absolute;
					width: 100%;
					height: 100%;
					border-radius: 50%;
					opacity: 0;

					&:checked + label {
						background: $Orange;
						color: $White;
					}
				}

				&:hover label {
					background: $Light-Grey;
					color: $White;
				}
			}
		}

		button[type='submit'] {
			outline: none;
			border: none;
			background: $Orange;
			color: $White;
			padding: 15px 0;
			border-radius: 99rem;
			font-size: 0.9em;
			text-transform: uppercase;
			letter-spacing: 0.1rem;
			font-weight: 700;
			cursor: pointer;
			transition: 0.2s ease-in-out;

			&:hover {
				background: $White;
				color: $Orange;
			}
		}
	}
}
</style>
