<template>
	<main>
		<p>{{ showLabel }}</p>
		<h1>{{ formatAmount }}</h1>
		<div class="graphic">
			<slot name="graphic"></slot>
		</div>
		<div class="action">
			<slot name="action"></slot>
		</div>
	</main>
</template>

<script>
const currencyAmount = new Intl.NumberFormat("es-SV", {
	style: "currency",
	currency: "USD",
});

export default {
	props: {
		label: {
			type: String,
			require: true,
		},
		valLabel: {
			type: String,
			default: null,
		},
		totalAmount: {
			type: Number,
			require: true,
		},
		amount: {
			type: Number,
			default: null,
		},
	},
	computed: {
		visualAmount() {
			return this.amount !== null ? this.amount : this.totalAmount;
		},
		showLabel() {
			return this.amount !== null ? this.label : this.valLabel;
		},
		formatAmount() {
			return currencyAmount.format(this.visualAmount);
		},
	},
};
</script>

<style scoped>
main {
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
	width: 100%;
}
h1,
p {
	margin: 0;
	text-align: center;
}
h1 {
	margin-top: 14px;
	color: var(--brand-green);
}
.graphic {
	display: flex;
	justify-content: center;
	align-items: center;
	width: 100%;
	padding: 48px 24px;
	box-sizing: border-box;
}
</style>
