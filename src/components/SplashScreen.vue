<template>
	<div class="splashscreen">
		<img src="@/assets/cashflow-icon.svg" alt="Logo de la app" />
		<h1><span>Money</span>Flow</h1>
	</div>
</template>

<style scoped>
.splashscreen {
	display: flex;
	justify-content: center;
	align-items: center;
	flex-direction: column;
	height: 100vh;
}
h1 {
	color: var(--brand-blue);
}
h1 span {
	color: var(--brand-green);
}
</style>
