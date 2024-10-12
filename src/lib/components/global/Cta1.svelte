<script>
	let { href = '/', content = 'Content' } = $props();
</script>

<a {href}>{content}</a>

<style>
	a {
		padding: 12px 22px;
		border-radius: 999px;
		border: 1px solid #f5f5f7;
		background: #f5f5f7;
		color: var(--black);
		display: inline-block;

		font-size: 16px;
		font-weight: 500;
		letter-spacing: -0.374px;

		transition: background-color 0.2s;

		&:hover {
			background-color: white;
		}
	}
</style>
