<script>
	import Marquee from '../lib/components/global/Marquee.svelte';
	import Hero from '../lib/components/pages/home/Hero.svelte';
	import Footer from '../lib/components/global/Footer.svelte';
</script>

<div id="home" class="w">
	<Hero />
	<Marquee />
</div>

<Footer />

<style>
	#home {
		padding-bottom: 200px;
	}
</style>
