<template>
	<div class="hub-server">
		<div v-dompurify-html="status" class="hub-server__status"></div>
		<div class="ml-4 text-center">
			<a :href="`byond://BYOND.world.${urlId}`" class="cta cta--sm px-10">
				Join
			</a>
			<div class="text-sm mt-2 italic">
				{{ players }}
				player<template v-if="players !== 1">s</template> online
			</div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		urlId: {
			type: String,
			required: true,
		},
		status: {
			type: String,
			required: true,
		},
		players: {
			type: Number,
			required: true,
		},
	},

	mounted() {
		const links = this.$el.querySelectorAll('a')
		for (const link of links) {
			link.setAttribute('target', '_blank')
		}
	},
}
</script>

<style lang="scss" scoped>
.hub-server {
	@apply flex justify-between text-sm px-4 py-3 border-b border-background;

	&:hover {
		@apply bg-background bg-opacity-20;
	}

	&__status {
		word-break: break-word;
	}
}
</style>

<style lang="scss">
.hub-server {
	img {
		display: inline;
		max-height: 200px;
	}
}
</style>
