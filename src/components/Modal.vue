<template>
		<div
			class="modal absolute"
			:class="{active: sendModalActive}"
		>
			<div class="container">
				<div class="row df jcc">
					<div class="modal-inner relative">
						<div
							class="modal-close absolute"
							@click="closeModal"
						>
							<img width="" src="img/modal-close.png">
						</div>
						<img
							class="modal-img"
							:src="sendModalImg"
						>
					</div>

				</div>
			</div>
		</div>
</template>

<script>
export default {
	name: 'Modal',
	props: ['sendModalActive', 'sendModalImg'],
	data() {
		return {
			modalActive: this.sendModalActive
		}
	},
	methods: {
		closeModal() {
			this.modalActive = false;
			this.$emit('modalWasClosed', this.modalActive);
		}
	}
}
</script>

<style lang="scss">
@import '../assets/scss/_bundled';
@import '../assets/scss/modules/_modal';
</style>