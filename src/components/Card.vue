<template>

	<div
		class="zc-item mb-20 relative"
		@click="clickedCard"
	>

		<div class="zc-item-card relative">
			<div class="zc-item-card-text df fdc jca">
				<div class="zc-item-card-label">
					<p>{{ sendIndex.replace('-', ' ') }}</p>
				</div>
				<div class="zc-item-card-caption">
					<p>{{ sendCard }}</p>
				</div>
			</div>

			<div class="zc-item-card-bottom absolute" :class="sendIndex"></div>
		</div>
		<div>
			<img class="zc-item-img" :src="sendImgUrl">
		</div>
	</div>


</template>

<script>
	export default {
		name: "Card",
		props: ["sendCard", "sendIndex", "sendImgUrl"],
		data() {
			return {
				activateModal: '',
				modalImage: ''

			}
		},
		methods: {
			clickedCard() {
				this.activateModal = true;
				this.modalImage = this.sendImgUrl;
				this.$emit('emitModalActivate', this.activateModal );
				this.$emit('emitModalImage', this.modalImage );
			}
		}

	}
</script>