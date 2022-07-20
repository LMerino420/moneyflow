<template>
	<MainLayout>
		<template #header>
			<MainHeader />
		</template>
		<template #resume>
			<MainResume />
		</template>
		<template #movements>
			<MainMovements />
		</template>
	</MainLayout>
</template>

<script>
import MainLayout from "./layout/MainLayout.vue";
import MainHeader from "./layout/MainHeader.vue";
import MainResume from "./layout/MainResume.vue";
import MainMovements from "./layout/MainMovements.vue";

export default {
	components: { MainLayout, MainHeader, MainResume, MainMovements },
};
</script>
