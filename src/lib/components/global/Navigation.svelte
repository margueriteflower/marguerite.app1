<script>
	import { page } from '$app/stores';
	import { menuTheme } from '../../../routes/store';
	import NavigationMobile from './NavigationMobile.svelte';

	let mobileOpen = $state(false);
</script>

<nav class={$menuTheme}>
	<div class="container">
		<div class="left">
			<a href="/" aria-label="go to home"><span></span></a>
		</div>

		<div class="right">
			<a href="/">Home <span class={$page.url.pathname === '/' ? 'visible' : ''}></span></a>
			<!-- <a href="/services"
				>Services <span class={$page.url.pathname === '/services' ? 'visible' : ''}></span></a
			>
			<a href="/buildinpublic"
				>Build In Public <span class={$page.url.pathname === '/buildinpublic' ? 'visible' : ''}
				></span></a
			>
			<a href="/blog"
				>Blog <span class={$page.url.pathname === '/blog' ? 'visible' : ''}></span>
			</a>
			<a href="/free-audit">Free Audit</a> -->
			<a href="/contact">Contact</a>

			<button onclick={() => (mobileOpen = true)}>Menu</button>
		</div>
	</div>
</nav>

<NavigationMobile bind:open={mobileOpen} />

<style>
	nav {
		backdrop-filter: blur(10px);

		display: flex;
		justify-content: center;
		height: 52px;
		width: 100%;

		font-size: 12px;
		position: fixed;
		top: 0;
		left: 0;
		z-index: 999;

		transition: background 0.2s;
	}

	nav.black {
		background: rgba(29, 29, 31, 0.8);
		color: var(--white);

		& a:hover {
			color: rgb(203, 203, 203);
		}

		& a[href='/free-audit'] {
			border: 1px solid var(--white);
		}

		.left a span {
			background-image: url('/logo/m50-white.png');
		}
	}

	nav.white {
		color: var(--black);
		background: rgba(255, 255, 255, 0.8);
		& a:hover {
			color: var(--grey2);
		}

		.left a span {
			background-image: url('/logo/m50-black.png');
		}
	}

	nav.grey {
		background: rgba(245, 245, 247, 0.8);
		color: var(--black);
		& a:hover {
			color: var(--grey2);
		}

		.left a span {
			background-image: url('/logo/m50-black.png');
		}
	}

	.container {
		width: 980px;
		height: 100%;
		display: flex;
		justify-content: space-between;
	}

	.left {
		display: flex;
		align-items: center;
		justify-content: flex-start;

		a {
			padding: 10px;
		}

		a span {
			background-size: 16px 16px;
			background-repeat: no-repeat;
			background-position: center;
			width: 16px;
			height: 16px;
			display: block;
		}
	}

	.right {
		display: flex;
		gap: 10px;
		align-items: center;

		a {
			transition: all 0.2s;

			position: relative;
			padding: 10px;
		}

		span {
			width: 5px;
			height: 5px;
			border-radius: 999px;
			background-color: var(--blue);
			position: absolute;
			left: 50%;
			bottom: 1px;
			transform: translateX(-50%);
			opacity: 0;
			transform: translateY(-2px);
			transition: all 0.3s;

			&.visible {
				opacity: 1;
				transform: translateY(0px) translateX(-50%);
			}
		}

		& a[href='/contact'] {
			background-color: var(--blue);
			padding: 4px 11px;
			color: var(--white);
			border-radius: 999px;

			&:hover {
				background-color: var(--blue2);
				color: var(--white);
			}
		}

		& a[href='/free-audit'] {
			border-radius: 999px;
			border: 1px solid var(--black);
			padding: 3px 10px;

			&:hover {
				background-color: white;
				border: 1px solid var(--white);
				color: var(--black);
			}
		}

		button {
			display: none;
		}
	}

	.mobile-menu {
		display: none;
	}

	@media (max-width: 1024px) {
		.container {
			padding: 20px;
		}

		.left a {
			padding-left: 0;
		}
	}

	@media (max-width: 768px) {
		.right button {
			display: block;
			transition: color 0.2s;

			&:hover {
				color: rgb(203, 203, 203);
			}
		}

		.right a {
			display: none;
		}
	}
</style>
