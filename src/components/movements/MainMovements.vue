<template>
	<div class="movements">
		<h2 class="title">Historial</h2>
		<div class="content">
			<UniMovement
				v-for="{ id, title, description, amnt } in movements"
				:key="id"
				:id="id"
				:title="title"
				:description="description"
				:amnt="amnt"
				@remove="remove"
			/>
		</div>
	</div>
</template>

<script setup>
import { toRefs, defineProps, defineEmits } from "vue";
import UniMovement from "./UnitMovement.vue";

const props = defineProps({
	movements: {
		type: Array,
		default: () => [],
	},
});

const { movements } = toRefs(props);
const emit = defineEmits("remove");

const remove = (id) => {
	emit("remove", id);
};
</script>

<style scoped>
.movements {
	max-height: 100%;
	padding: 0 8px;
	margin-bottom: 14px;
}
.title {
	margin: 8px 16px 24px 16px;
	color: var(–brand-blue);
}
.content {
	max-height: 68vh;
	display: flex;
	flex-direction: column;
	gap: 8px;
	overflow-y: scroll;
}
</style>
