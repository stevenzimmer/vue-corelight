<template>
	<section class="zc-body relative">
		<div class="container">
			<div class="row df jcb fww mb-40 zc-body-row">

				<!-- Cards -->
				<Card
					v-for="(card, index) in cards"
					:sendCard="card"
					:sendIndex="index"
					:sendImgUrl="getImgUrl(index)"
					@emitModalActivate="modalActive = $event"
					@emitModalImage="modalImg = $event"
				></Card>


				<!-- Download -->
				<Download></Download>

			</div>
		</div>
		<Modal
			:sendModalActive="modalActive"
			:sendModalImg="modalImg"
			@modalWasClosed="modalActive = $event"
		>
		</Modal>

	</section>
</template>

<script>
import Modal from './Modal';
import Card from './Card';
import Download from './Download';

export default {
	name: 'Main',
	components: {
		Modal,
		Card,
		Download
	},
	props: ['sendCurrentPage'],
	data() {
		return {
			logs: {
				popular: {
					"conn": 'IP, TCP, UDP, ICMP, connection details',
					"conn-history" : "Orig UPPERCASE, Resp, lowercase, compressed",
					"conn-state": "A summarised state for each connection",
					"dns": "DNS query/response details",
					"http": "HTTP request/reply details"
				},
				smb: {
					"dce-rpc": "Details on DCE/RPC messages",
					"ntlm": "NT LAN Manager (NTLM)",
					"rdp": "Remote Desktop Protocol",
					"smb-files": "Details on SMB files",
					"smb-mappings": "SMB mappings"
				}
			},
			cards: {},
			modalImg: '',
			modalActive: false
		}
	},
	methods: {
		getImgUrl( img ) {
			return 'img/' + img + '.png';
		},
		clickedCard(img) {
			this.modalActive = true;
			this.modalImg = this.getImgUrl(img)
		}
	},
	watch: {

		sendCurrentPage( value ) {

			if ( value === 'all' ) {

				this.cards = Object.assign( {}, this.logs.popular, this.logs.smb);

			} else {
				this.cards = this.logs[value]
			}
		},
		modalImg( value ) {
			console.log('modal Image ', value );
		}
	},
	mounted() {
		this.cards = this.logs[this.sendCurrentPage];
	}
};
</script>

<style lang="scss">
@import '../assets/scss/_bundled';
@import '../assets/scss/modules/_main';
</style>