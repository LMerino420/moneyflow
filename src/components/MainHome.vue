<template>
	<MainLayout>
		<template #header>
			<MainHeader />
		</template>
		<template #resume>
			<MainResume :label="'Ahorro total'" :valLabel="valLabel" :amount="valAmount" :totalAmount="totAmount">
				<template #graphic>
					<MainGraphic :amounts="amnts"></MainGraphic>
				</template>
				<template #action>
					<ActionForm @create="create" />
				</template>
			</MainResume>
		</template>
		<template #movements>
			<MainMovements :movements="arMovements" @remove="remove" />
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
			arMovements: [],
		};
	},
	computed: {
		amnts() {
			const lastDays = this.arMovements
				.filter((m) => {
					const today = new Date();
					const oldDate = today.setDate(today.getDate() - 30);

					return m.time > oldDate;
				})
				.map((m) => m.amnt);

			return lastDays.map((m, i) => {
				const lastMove = lastDays.slice(0, i);
				return lastMove.reduce((sum, mov) => {
					return sum + mov;
				}, 0);
			});
		},
		totAmount() {
			return this.arMovements.reduce((sum, m) => {
				return sum + m.amnt;
			}, 0);
		},
	},
	mounted() {
		const mov = JSON.parse(localStorage.getItem("movimientos"));
		if (Array.isArray(mov)) {
			this.arMovements = mov.map((m) => {
				return { ...m, time: new Date(m.time) };
			});
		}
	},
	methods: {
		create(movement) {
			this.arMovements.push(movement);
			this.save();
		},
		remove(id) {
			const index = this.arMovements.findIndex((m) => m.id === id);
			this.arMovements.splice(index, 1);
			this.save();
		},
		save() {
			localStorage.setItem("movimientos", JSON.stringify(this.arMovements));
		},
	},
};
</script>
