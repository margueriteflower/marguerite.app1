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

<div id="footer" bind:this={component}>
	<div class="wrapper">
		<div class="index">
			<img src="/logo/m50-black.png" alt="Marguerite logo" />
			<svg xmlns="http://www.w3.org/2000/svg" width="6" height="12" viewBox="0 0 6 12" fill="none">
				<g clip-path="url(#clip0_14_300)">
					<path
						d="M0.674805 1.01465L5.3228 5.58965L0.674805 10.1646"
						stroke="rgba(0, 0, 0, 0.48)"
						stroke-width="1.1"
						stroke-linecap="round"
						stroke-linejoin="round"
					/>
				</g>
				<defs>
					<clipPath id="clip0_14_300">
						<rect width="6" height="11" fill="white" transform="translate(0 0.0898438)" />
					</clipPath>
				</defs>
			</svg>
			<div class="title">Footer</div>
		</div>

		<div class="description">
			<strong> At Marguerite </strong>, we’re all about <strong>scaling your business.</strong>
			We’re not just a web agency focused on design or development — <br />
			we aim to drive growth and help you make more money. If you’re ready to level up, we’re here to
			make it happen.
		</div>

		<div class="list">
			<div class="top">Marguerite</div>
			<div class="bottom">
				<ul>
					<li class="title">Work</li>
					<li>Available Soon</li>
					<li>Available Soon</li>
					<li>Available Soon</li>
				</ul>

				<ul>
					<li class="title">Services</li>
					<li>Audit</li>
					<li>Web Design</li>
					<li>Web Development</li>
					<li>SEO</li>
					<li>Consulting</li>
				</ul>

				<ul>
					<li class="title">Build In Public</li>
					<li>Earn</li>
					<li>Success Stories</li>
					<li>Videos</li>
				</ul>

				<ul>
					<li class="title">Socials</li>
					<a href="https://x.com/margueriteweb" target="_blank">X</a>
					<a href="https://www.linkedin.com/company/marguerite-app" target="_blank">Linkedin</a>
					<li>Youtube (soon)</li>
				</ul>

				<ul>
					<li class="title">contact</li>
					<a href="mailto:contact@marguerite.app">contact@marguerite.app</a>
				</ul>
			</div>
		</div>

		<div class="foot">
			<div class="top">
				<p>Where smart businesses come to scale and make serious money.</p>
				<a href="mailto:contact@marguerite.app">contact us.</a>
			</div>

			<div class="bottom">
				<p>Copyright © 2024 Marguerite. All rights reserved.</p>
				<p>France</p>
			</div>
		</div>
	</div>
</div>

<style>
	#footer {
		position: sticky;
		height: calc(100svh);
		z-index: 99;
		background: rgba(255, 255, 255, 1);
		will-change: transform;
		box-shadow: 0px -4px 40px 0px rgba(0, 0, 0, 0.05);
	}

	.wrapper {
		width: 980px;
		margin: auto;
		padding-top: 40px;
	}

	a {
		color: var(--blue);
		font-size: 12px;
		font-weight: 400;
		text-decoration-line: underline;
	}

	.index {
		display: flex;
		align-items: center;
		gap: 10px;

		img {
			width: 11px;
		}

		.title {
			color: rgba(0, 0, 0, 0.72);
			font-size: 12px;
		}
	}

	.description {
		margin-top: 150px;
		color: rgba(0, 0, 0, 0.56);
		font-size: 14px;
		font-weight: 400;
		width: 587px;

		strong {
			color: rgba(0, 0, 0, 0.76);
			font-size: 14px;
			font-weight: 400;
		}
	}

	.list {
		overflow: hidden;

		.top {
			color: rgba(0, 0, 0, 0.04);
			font-family: Inter;
			font-size: 205px;
			font-style: normal;
			font-weight: 400;
			line-height: normal;
			letter-spacing: -0.12px;

			position: relative;
			top: 86px;

			width: 980px;
		}

		.bottom {
			display: flex;

			background: #fff;
			box-shadow: 0px -4px 40px 0px rgba(0, 0, 0, 0.05);
			/* border-top: 1px solid rgba(0, 0, 0, 0.16); */
			position: relative;
			z-index: 10;
		}

		ul {
			color: rgba(0, 0, 0, 0.72);
			font-family: Inter;
			font-size: 12px;
			font-style: normal;
			font-weight: 400;
			line-height: 16px; /* 135.45% */
			letter-spacing: -0.12px;
			list-style-type: none;

			display: flex;
			flex-direction: column;
			gap: 10px;

			padding-left: 0;
			margin-top: 32px;

			width: 170px;

			.title {
				color: rgba(0, 0, 0, 0.88);
				font-size: 12px;
				font-weight: 600;
			}
		}
	}

	.foot {
		position: absolute;
		bottom: 0;
		width: 100%;

		width: 980px;

		color: rgba(0, 0, 0, 0.56);
		font-size: 12px;
		font-style: normal;
		font-weight: 400;

		& > div {
			height: 48px;
		}

		.top {
			display: flex;
			align-items: center;
			gap: 10px;
		}

		.bottom {
			display: flex;
			justify-content: space-between;
			align-items: center;
			width: 100%;

			border-top: 1px solid rgba(0, 0, 0, 0.16);
		}
	}
</style>
