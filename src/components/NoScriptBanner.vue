<template>
	<noscript inline-template>
		<div role="status">
			<p>Search and Darkmode require Javascript. <g-link to='/'>All books</g-link>.</p>
		</div>
	</noscript>
</template>

<script>
	export default {};
</script>

<style scoped>
	div
	{
		color: var(--grey-10);
		font-size: var(--md-text);
		font-style: italic;
		letter-spacing: 0.025em;

		background: var(--grey-40);
		padding: 6px 40px;

		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		z-index: 999;
	}

	a
	{
		color: inherit;
		text-decoration: none;

		background-image: linear-gradient(var(--grey-10), var(--grey-10));
		background-size: 100% 1px;
		background-position: left bottom;
		background-repeat: no-repeat;
	}
</style>
