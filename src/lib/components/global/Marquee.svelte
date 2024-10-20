<script>
	import gsap from 'gsap';
	import { onMount } from 'svelte';

	let ctx = $state();
	let component = $state();
	let tl = $state();
	let hoverTiming = 60;
	let normalTiming = 40;

	onMount(() => {
		const moving = component.querySelector('.moving');
		const cards = component.querySelectorAll('.card');
		const totalWidth = Array.from(cards).reduce((acc, card) => acc + card.offsetWidth + 10, 0);

		// Cloner le contenu pour le défilement infini
		moving.innerHTML += moving.innerHTML;

		ctx = gsap.context((e) => {
			tl = gsap.timeline({ repeat: -1, ease: 'none' });
			tl.to('.moving', {
				x: -totalWidth,
				duration: normalTiming,
				ease: 'linear'
			});
		}, component);

		return () => ctx.revert();
	});

	const pointerenter = () => {
		tl.duration(hoverTiming);
	};

	const pointerleave = () => {
		tl.duration(normalTiming);
	};
</script>

<div
	class="marquee"
	bind:this={component}
	onpointerenter={pointerenter}
	onpointerleave={pointerleave}
>
	<div class="moving">
		{#each Array(7) as _, i}
			<a href="/" class="card">
				<div class="picture">
					<button>Coming Soon</button>
					<!-- <button>Link {i}</button> -->
				</div>
				<div class="text">
					<h2>Work {i}</h2>
					<p>Coming Soon</p>
				</div>
			</a>
		{/each}
	</div>
</div>

<style>
	.marquee {
		overflow: hidden;
		white-space: nowrap;
		width: 100%;
		margin-top: 20px;
		font-size: 14px;
	}

	.moving {
		display: flex;
		gap: 10px;
	}

	.card {
		width: 234px;
		flex-shrink: 0;
		cursor: pointer;

		&:hover button {
			opacity: 1;
			transform: translate(-50%, -50%);
		}

		&:hover .picture {
			background-color: rgba(162, 162, 162, 0.31);
		}
	}

	.picture {
		transition: background-color 0.2s;
		aspect-ratio: 1;
		width: 100%;
		background-color: rgba(227, 227, 227, 0.51);
		position: relative;
		border-radius: 6px;

		border: 1px solid rgba(227, 227, 227, 0.7);
	}

	button {
		transition: all 0.2s;

		border-radius: 999px;
		background: var(--white);
		padding: 12px 22px;
		font-weight: 600;
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -40%);
		opacity: 0;
	}

	h2 {
		letter-spacing: -0.224px;
		font-size: 14px;
		font-weight: 400;
		color: var(--black);

		margin: 0;
		margin-top: 10px;
	}

	p {
		color: var(--grey2);
		margin: 0;
		margin-top: 10px;
		font-size: 14px;
	}

	@media (max-width: 1024px) {
		.card {
			width: 150px;
		}
	}

	/* @media (max-width: 768px) {
		.card {
			width: 260px;
		}
	} */
</style>
