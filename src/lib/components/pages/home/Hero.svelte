<script>
	import gsap from 'gsap';
	import { onMount } from 'svelte';

	let ctx = $state();
	let component = $state();
	let videoState = $state('playing'); // playing or paused
	let video = $state();

	onMount(() => {
		ctx = gsap.context(() => {}, component);

		return () => ctx.revert();
	});

	function videoController() {
		if (videoState === 'playing') {
			videoState = 'paused';

			video.pause();

			gsap.set('.pause', { opacity: 0 });
			gsap.set('.play', { opacity: 1 });
		} else if (videoState === 'paused') {
			videoState = 'playing';

			video.play();

			gsap.set('.pause', { opacity: 1 });
			gsap.set('.play', { opacity: 0 });
		}
	}
</script>

<div class="hero">
	<!-- <div class="overlay">
		<div class="center">
			<div class="text">
				<div class="top">
					<img src="/favicon.png" alt="icon marguerite" />
					<p>Marguerite</p>
				</div>

				<div class="bottom">
					<h1>Why Choosing the Right Agency Matters for Your Success.</h1>

					<div class="ctas">
						<Cta1 content={'Discover why'} />
					</div>
				</div>
			</div>
		</div>
	</div> -->

	<!-- <img src="/pages/home/hero.jpg" alt="hero" /> -->

	<video src="/pages/home/large.mp4" autoplay muted loop bind:this={video}></video>

	<button aria-label="play-pause" onclick={videoController}>
		<svg class="pause" xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16"
			><path
				fill="white"
				d="M4.5 2a.5.5 0 0 0-.5.5v11a.5.5 0 0 0 .5.5h1a.5.5 0 0 0 .5-.5v-11a.5.5 0 0 0-.5-.5zm6 0a.5.5 0 0 0-.5.5v11a.5.5 0 0 0 .5.5h1a.5.5 0 0 0 .5-.5v-11a.5.5 0 0 0-.5-.5z"
			/></svg
		>

		<svg class="play" xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16"
			><path
				fill="white"
				d="M3 3.732a1.5 1.5 0 0 1 2.305-1.265l6.706 4.267a1.5 1.5 0 0 1 0 2.531l-6.706 4.268A1.5 1.5 0 0 1 3 12.267z"
			/></svg
		>
	</button>
</div>

<style>
	.hero {
		height: 70svh;
		width: 100vw;
		position: relative;
		/* margin-top: 52px; */

		/* & > img {
			filter: brightness(0.8);
		} */

		& > video {
			width: 100%;
			height: 100%;
			object-fit: cover;
		}
	}

	button {
		border-radius: 999px;
		border: 1px solid white;
		display: flex;
		align-items: center;
		justify-content: center;

		width: 34px;
		height: 34px;

		position: absolute;
		right: 40px;
		bottom: 40px;

		svg {
			position: absolute;
			top: 50%;
			left: 50%;
			transform: translate(-50%, -50%);
		}

		.play {
			opacity: 0;
			left: calc(50% + 1px);
		}
	}

	/* .overlay {
		background: linear-gradient(
			0deg,
			#ffffff 0%,
			rgba(0, 0, 0, 0.2) 28.56%,
			rgba(255, 255, 255, 0) 57.29%
		);

		position: absolute;
		inset: 0;

		display: flex;
		flex-direction: column;
		justify-content: flex-end;
		z-index: 99;
	}

	.center {
		width: 980px;
		margin: 0 auto;
	}

	img {
		width: 100%;
		height: 100%;
		object-fit: cover;
	}

	.text {
		color: var(--white);
		margin-bottom: 40px;

		.top {
			display: flex;
			align-items: center;
			gap: 5px;
			img {
				width: 24px;
				height: 24px;
			}

			p {
				font-size: 17px;
				font-weight: 500;

				color: #f5f5f7;
				margin-right: 18px;
			}
		}

		.bottom {
			display: flex;
			justify-content: space-between;
			align-items: end;

			h1 {
				font-size: 36px;
				font-weight: 700;
				width: 600px;
				margin: 0;
			}

			.ctas {
				height: fit-content;
			}
		}
	}

	@media (max-width: 1024px) {
		.center {
			padding: 0 20px;
			width: 100%;
		}
		.text {
			margin-bottom: 50px;
			.bottom {
				flex-direction: column;
				align-items: start;
				gap: 20px;

				h1 {
					width: 100%;

					font-size: 24px;
				}
			}
		}
	} */
</style>
