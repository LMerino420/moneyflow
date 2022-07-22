<template>
	<MainLayout>
		<template #header>
			<MainHeader />
		</template>
		<template #resume>
			<MainResume :label="'Ahorro total'" :valLabel="valLabel" :amount="valAmount" :totalAmount="1610960">
				<template #graphic>
					<MainGraphic :amounts="amnts"></MainGraphic>
				</template>
				<template #action>
					<ActionForm />
				</template>
			</MainResume>
		</template>
		<template #movements>
			<MainMovements :movements="arMovements" />
		</template>
	</MainLayout>
</template>

<script>
import MainLayout from "./layout/MainLayout.vue";
import MainHeader from "./layout/MainHeader.vue";
import MainResume from "./layout/MainResume.vue";
import MainMovements from "./movements/MainMovements.vue";
import ActionForm from "./addmovement/ActionForm.vue";
import MainGraphic from "./layout/MainGraphic.vue";

export default {
	components: { MainLayout, MainHeader, MainResume, MainMovements, ActionForm, MainGraphic },
	data() {
		return {
			valAmount: null,
			valLabel: null,
			amnts: [420, 1200, 800, -450, -150, 1800],
			arMovements: [
				{
					id: 0,
					title: "Prueba 0",
					description: "lorem ipsum dolor sit amet",
					amnt: 1000,
				},
				{
					id: 1,
					title: "Prueba 1",
					description: "lorem ipsum dolor sit amet",
					amnt: 1000,
				},
				{
					id: 2,
					title: "Prueba 2",
					description: "lorem ipsum dolor sit amet",
					amnt: 1000,
				},
				{
					id: 3,
					title: "Prueba 3",
					description: "lorem ipsum dolor sit amet",
					amnt: -1000,
				},
			],
		};
	},
};
</script>
