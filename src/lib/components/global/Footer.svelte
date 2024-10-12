<script>
	import ScrollTrigger from 'gsap/dist/ScrollTrigger';
	import { onMount } from 'svelte';
	import gsap from 'gsap';

	let ctx = $state();
	let component = $state();

	onMount(() => {
		gsap.registerPlugin(ScrollTrigger);

		let oSetter = gsap.utils.pipe(
			gsap.quickSetter('.w', 'opacity') //apply it to the #id element's x property and append a "px" unit
		);

		ctx = gsap.context(() => {
			// footer sticky
			gsap.to('#footer', {
				scrollTrigger: {
					trigger: '#footer',
					start: 'top bottom',
					end: 'bottom bottom',
					scrub: true,
					onEnter: () => {
						gsap.set('.w', {
							position: 'sticky',
							top: -scrollY
						});
					},
					onLeaveBack: () => {
						gsap.set('.w', {
							position: 'static',
							top: 0
						});
					},
					onUpdate: (self) => {
						oSetter(1 - self.progress * 0.9);
					}
				}
			});
		});

		return () => {
			ctx.revert();
			ScrollTrigger.killAll();
		};
	});
</script>

<div id="footer" bind:this={component}></div>

<style>
	#footer {
		padding-top: 50px;
		position: sticky;
		height: calc(100svh);
		z-index: 99;
		background: rgba(255, 255, 255, 1);
		will-change: transform;
		box-shadow: 0px -4px 40px 0px rgba(0, 0, 0, 0.05);
	}
</style>
