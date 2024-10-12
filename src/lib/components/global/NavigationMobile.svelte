<script>
	import { onMount } from 'svelte';
	import { menuTheme } from '../../../routes/store';
	import gsap from 'gsap';

	let { open = $bindable(false) } = $props();

	let ctx = $state(),
		component = $state();

	onMount(() => {
		ctx = gsap.context(() => {}, component);

		return () => ctx.revert();
	});

	const animateIn = (node) => {
		ctx.add(() => {
			gsap.fromTo(node, { opacity: 0 }, { opacity: 1 });

			gsap.fromTo('.bottom a', { y: -20, opacity: 0 }, { y: 0, stagger: 0.03, opacity: 1 });
		});
	};

	const animateOut = (node) => {
		ctx.add(() => {
			gsap.to(node, { opacity: 0 });
		});

		return { duration: 0.5 * 1000 };
	};
</script>

{#if open}
	<nav class="mobile-menu {$menuTheme}" in:animateIn out:animateOut bind:this={component}>
		<div class="top"><button onclick={() => (open = false)}>Close</button></div>

		<div class="bottom">
			<a href="/" onclick={() => (open = false)}>Home</a>
			<a href="/services" onclick={() => (open = false)}>Services</a>
			<a href="/buildinpublic" onclick={() => (open = false)}>Build In Public</a>
			<a href="/blog" onclick={() => (open = false)}>Blog</a>
			<a href="/free-audit" onclick={() => (open = false)}>Free Audit</a>
			<a href="/contact" onclick={() => (open = false)}>Contact</a>
		</div>
	</nav>
{/if}

<style>
	.mobile-menu {
		display: block;
		position: fixed;
		top: 0;
		left: 0;
		height: 100svh;
		width: 100vw;
		background-color: white;
		z-index: 999;
	}

	.mobile-menu.black {
		background-color: rgb(0, 0, 0);
		color: var(--white);

		.bottom a:hover {
			color: rgb(203, 203, 203);
		}

		.top button:hover {
			color: rgb(203, 203, 203);
		}
	}

	.top {
		height: 50px;
		padding: 20px;
		display: flex;
		align-items: center;
		justify-content: flex-end;
		font-size: 12px;

		button {
			transition: color 0.2s;
		}
	}

	.bottom {
		display: flex;
		flex-direction: column;
		gap: 15px;
		margin-top: 20px;
		margin-left: 50px;
		a {
			font-size: 28px;
			font-weight: 600;
			transition: color 0.2s;
		}
	}
</style>
