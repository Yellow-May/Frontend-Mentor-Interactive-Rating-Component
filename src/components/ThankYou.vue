<script lang="ts">
import { defineComponent } from 'vue';
import type { PropType } from 'vue';
export default defineComponent({
	props: {
		selected_rating: { type: String as PropType<'1' | '2' | '3' | '4' | '5'>, required: true },
	},
});
</script>

<template>
	<section class="thank-you">
		<div class="logo">
			<img src="../assets/images/illustration-thank-you.svg" alt="thank you" />
		</div>

		<div class="you-selected">
			<span>You selected {{ selected_rating }} out of 5</span>
		</div>

		<div class="appreciation-text">
			<h1>Thank you!</h1>

			<p>
				We appreciate you taking the time to give a rating. If you ever need more support, don’t hesitate to get in touch!
			</p>
		</div>
	</section>
</template>

<style lang="scss" scoped>
@import '../assets/scss/variables.scss';

section.thank-you {
	height: 100%;
	padding: 24px;
	padding-bottom: 40px;
	display: flex;
	flex-direction: column;
	justify-content: space-between;
	align-items: center;
	gap: 24px;

	.you-selected {
		padding: 8px 16px;
		border-radius: 99rem;
		background: rgba($Medium-Grey, 0.1);

		span {
			font-size: 0.95em;
			font-weight: 400;
			color: $Orange;
			opacity: 0.8;
		}
	}

	.appreciation-text {
		text-align: center;
		display: grid;
		gap: 16px;

		h1 {
			color: $White;
		}

		p {
			color: $Medium-Grey;
			line-height: 1.6;
		}
	}
}
</style>
