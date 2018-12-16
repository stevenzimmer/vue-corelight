<template>
  <div id="app" class="relative">
    <Nav
    	@navWasChanged="currentPage = $event"
    />
    <Main
    	:sendCurrentPage="currentPage"
    >
    </Main>

  </div>
</template>

<script>
import Nav from './components/Nav';
import Main from './components/Main';

export default {
  name: 'App',
  components: {
    Nav,
    Main
  },
  data() {
  	return {
  		currentPage: 'popular',
  	}
  },
  watch: {
    currentPage(  ) {
      // console.log('currentPage ', value );
    }
  },

  // Hooks
  // beforeCreate() {
  //   console.log('beforeCreate');
  // },

  // created() {
  //   console.log('created');
  // },

  // beforeMount() {
  //   console.log('before mount');
  // },

  // mounted() {
  //   console.log('mounted');
  // },

  // beforeUpdate() {
  //   console.log('before Update');
  // },

  // updated() {
  //   console.log('updated');
  // },

  // destroy() {
  //   console.log('destroy');
  // }

}
</script>

<style lang="scss">
  @import './assets/scss/_bundled';

</style>


