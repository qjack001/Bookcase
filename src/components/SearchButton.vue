<template>
	<g-link :to="'/'" class="search-button">
		<svg class="icon" role="presentation" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 38.537 34.109">
			<path d="M4.02 16.141a10 10 0 0119.405-4.838 9.926 9.926 0 01-.584 6.526l11.151 6.7-1.212 2.017-11.15-6.7a10 10 0 01-13.058 2.448 9.935 9.935 0 01-4.553-6.153zm7.852-9.838a7.647 7.647 0 103.7 14.839 7.647 7.647 0 10-3.7-14.84z"/>
		</svg>
		<p role="tooltip">Search</p>
	</g-link>
</template>

<script>
	export default {};
</script>

<style scoped>
	.search-button
	{
		position: relative;
		display: grid;
		grid-template-columns: 3rem 7.5rem;
		grid-template-rows: 3rem;
		height: 3rem;

		box-sizing: border-box;
		padding: 20px 30px;

		text-decoration: none;
		color: var(--grey-10);
	}

	.search-button:hover,
	.search-button:focus
	{
		color: var(--grey-00);
		outline: none;
	}

	.search-button:focus-visible::after
	{
		content: "";
		display: block;
		position: absolute;
		top: 10px;
		left: 10px;
		width: 21ch;
		height: 4.2rem;

		border: 2px solid var(--grey-10);
		border-radius: 4px;

		pointer-events: none;
	}

	.icon
	{
		fill: currentColor;
		width: 2.5rem;
		margin-top: 0.5rem;
	}

	p
	{
		font-size: var(--md-text);
		font-style: italic;
		letter-spacing: 0.025em;
		line-height: 3rem;

		margin: 0;
	}
</style>
