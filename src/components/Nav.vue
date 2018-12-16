<template>
	<nav class="zc-nav">
		<div class="container">
			<div class="zc-nav-row df jcb aic">
				<div class="zc-nav-logo">
					<a href="https://corelight.com"><img src="../assets/img/corelight-logo.svg"></a>
				</div>
				<div class="zc-nav-title text-white">
					<p>Zeek cheatsheets</p>
				</div>
			</div>
			<div class="zc-nav-row">
				<div class="zc-nav-items-wrapper df jcb">
					<div
						v-for="( navItem, index ) in navMenu"
						class="zc-nav-item text-center relative"
						@click="currentNav = index"
						:class="{ active: index == currentNav }"
					>
						<div class="zc-nav-border zc-nav-border-left absolute"></div>
						<p>{{ navItem }}</p>
					</div>
				</div>
			</div>
		</div>
	</nav>

</template>

<script type="text/javascript">

export default {
	name: 'Nav',
	data() {
		return {
			navMenu: {
				popular: 'Popular',
				smb: 'SMB',
				all: 'All'
			},
			currentNav: 'popular',
			isActive: false
		}
	},
	watch: {
		currentNav(value) {
			this.$emit('navWasChanged', this.currentNav);
		}
	}
};
</script>

<style lang="scss">
@import '../assets/scss/_bundled';
@import '../assets/scss/modules/_nav';
</style>