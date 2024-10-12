<script>
	import gsap from 'gsap';
	import { onMount } from 'svelte';

	let ctx = $state();
	let component = $state();

	onMount(() => {
		ctx = gsap.context(() => {
			const tl = gsap.timeline();

			tl.fromTo(
				'img',
				{ scale: 0.6, opacity: 0 },
				{ scale: 1, opacity: 1, duration: 0.5, ease: 'back.out(4)', delay: 0.2 }
			);
			tl.to('img', { x: 130, duration: 1, ease: 'power2.inOut' });
			tl.to('img', { x: -100, duration: 2, ease: 'power2.inOut' });
			tl.fromTo('h2 span', { opacity: 0, y: 10 }, { opacity: 1, stagger: -0.08, y: 0 }, '-=1.3');
		}, component);

		return () => ctx.revert();
	});
</script>

<div class="soon" bind:this={component}>
	<div class="label">
		<img src="/logo/m50-black.png" alt="m of marguerite logo" />
		<h2>
			{#each ['C', 'o', 'm', 'i', 'n', 'g', ' ', 's', 'o', 'o', 'n'] as letter}
				{#if letter === ' '}
					<span style="width: 10px;">
						{letter}
					</span>
				{:else}
					<span>
						{letter}
					</span>
				{/if}
			{/each}
		</h2>
	</div>

	<!-- <svg
		width="1440"
		height="570"
		viewBox="0 0 1440 570"
		fill="none"
		xmlns="http://www.w3.org/2000/svg"
	>
		<g opacity="0.5" filter="url(#filter0_f_776_3097)">
			<path
				d="M625.832 406.959L-219.709 478.468C-237.828 480.001 -254.899 490.155 -265.414 505.654L-286.295 536.432C-308.908 569.763 -292.531 611.951 -254.746 617.701L64.5768 666.294C67.3496 666.716 70.1725 666.921 73.02 666.907L891.855 663.011C949.458 662.737 975.603 586.124 927.056 559.864L655.32 412.881C646.53 408.126 636.305 406.073 625.832 406.959Z"
				fill="#FD822A"
			/>
		</g>
		<g opacity="0.5" filter="url(#filter1_f_776_3097)">
			<path
				d="M1445.08 469.467L735.304 304.136C711.955 298.697 682.89 298.998 660.032 304.915L482.263 350.934C450.776 359.085 439.73 375.49 456.784 388.774L617.676 514.089C621.765 517.274 627.296 520.12 633.989 522.483L1304.2 759.105C1348.41 774.715 1418.41 763.365 1423.92 739.693L1480.37 497.068C1482.98 485.849 1469.22 475.091 1445.08 469.467Z"
				fill="#A3ECFA"
			/>
		</g>
		<g opacity="0.5" filter="url(#filter2_f_776_3097)">
			<path
				d="M1421.26 766.058L711.479 600.727C688.131 595.288 659.065 595.589 636.208 601.506L458.439 647.525C426.952 655.676 415.906 672.082 432.96 685.365L593.852 810.68C597.941 813.865 603.472 816.711 610.165 819.074L1280.37 1055.7C1324.59 1071.31 1394.59 1059.96 1400.1 1036.28L1456.54 793.659C1459.15 782.441 1445.4 771.682 1421.26 766.058Z"
				fill="#C639F3"
			/>
		</g>
		<g opacity="0.5" filter="url(#filter3_f_776_3097)">
			<path
				d="M454.542 554.963L-281.969 731.26C-299.358 735.422 -308.504 747.102 -306.133 762.117L-298.496 810.487C-293.994 838.999 -251.224 867.583 -212.311 868.086L134.55 872.573C138.253 872.62 141.812 872.402 145.179 871.921L943.709 757.809C997.3 750.15 973.809 689.408 910.494 671.921L493.977 556.882C479.708 552.941 465.815 552.265 454.542 554.963Z"
				fill="#F22D34"
			/>
		</g>
		<defs>
			<filter
				id="filter0_f_776_3097"
				x="-596.607"
				y="106.758"
				width="1849.07"
				height="860.15"
				filterUnits="userSpaceOnUse"
				color-interpolation-filters="sRGB"
			>
				<feFlood flood-opacity="0" result="BackgroundImageFix" />
				<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape" />
				<feGaussianBlur stdDeviation="150" result="effect1_foregroundBlur_776_3097" />
			</filter>
			<filter
				id="filter1_f_776_3097"
				x="148.793"
				y="0.257324"
				width="1631.89"
				height="1066.03"
				filterUnits="userSpaceOnUse"
				color-interpolation-filters="sRGB"
			>
				<feFlood flood-opacity="0" result="BackgroundImageFix" />
				<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape" />
				<feGaussianBlur stdDeviation="150" result="effect1_foregroundBlur_776_3097" />
			</filter>
			<filter
				id="filter2_f_776_3097"
				x="124.969"
				y="296.848"
				width="1631.89"
				height="1066.03"
				filterUnits="userSpaceOnUse"
				color-interpolation-filters="sRGB"
			>
				<feFlood flood-opacity="0" result="BackgroundImageFix" />
				<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape" />
				<feGaussianBlur stdDeviation="150" result="effect1_foregroundBlur_776_3097" />
			</filter>
			<filter
				id="filter3_f_776_3097"
				x="-606.502"
				y="253.338"
				width="1879.96"
				height="919.241"
				filterUnits="userSpaceOnUse"
				color-interpolation-filters="sRGB"
			>
				<feFlood flood-opacity="0" result="BackgroundImageFix" />
				<feBlend mode="normal" in="SourceGraphic" in2="BackgroundImageFix" result="shape" />
				<feGaussianBlur stdDeviation="150" result="effect1_foregroundBlur_776_3097" />
			</filter>
		</defs>
	</svg> -->
</div>

<style>
	.soon {
		display: flex;
		align-items: center;
		justify-content: center;
		height: 100svh;
		position: relative;
		color: var(--black);
	}

	.label {
		display: flex;
		gap: 5px;
		align-items: center;
		width: 221px;
		position: relative;
		justify-content: center;
	}

	img {
		height: 26px;
		width: 26px;
		will-change: transform;
	}

	h2 {
		font-size: 32px;
		font-weight: 500;
		letter-spacing: -1.344px;
		position: absolute;
		right: 0;

		span {
			display: inline-block;
			will-change: transform;
		}
	}
</style>
