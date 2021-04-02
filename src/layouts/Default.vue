<template>
	<div>
		<slot/>
		<footer>
			<p>
				<g-link :to="'/about'">What is this?</g-link>
				• Jack Guinane &copy; 2021
			</p>
		</footer>
	</div>
</template>

<script>
	export default {}
</script>

<style>
	:root
	{
		--grey-00: #242424;
		--grey-10: #707070;
		--grey-20: #C2C4C3;
		--grey-30: #E4E4E4;
		--grey-40: #F7F7F7;
		--grey-50: #FFFFFF;

		--lg-text: 4.00rem;
		--md-text: 1.50rem;
		--sm-text: 0.75rem;
	}

	.darkmode
	{
		--grey-00: #dedede;
		--grey-10: #c3c3c3;
		--grey-20: #828282;
		--grey-30: #3d3d3d;
		--grey-40: #1a1a1a;
		--grey-50: #292929;
	}

	html
	{
		font-family: 'Times New Roman', Times, serif;
		font-size: 16px;
		line-height: 1.2;

		text-rendering: optimizeLegibility;
		-webkit-font-smoothing: antialiased; 
		-moz-osx-font-smoothing: grayscale;

		-moz-font-feature-settings:"kern" 1;
		-ms-font-feature-settings:"kern" 1;
		-o-font-feature-settings:"kern" 1;
		-webkit-font-feature-settings:"kern" 1;
		font-feature-settings:"kern" 1;
		font-kerning: normal;         
	}

	body
	{
		background-color: var(--grey-40);
		color: var(--grey-00);

		margin: 0;
		padding: 0;
	}

	footer
	{
		color: var(--grey-10);
		font-size: var(--sm-text);
		font-style: italic;
		text-align: right;

		padding: 20px;
	}

	footer a
	{
		color: inherit;
		text-decoration: none;
		border-bottom: 1px solid;
	}

	@media (prefers-reduced-motion)
	{
		*, *::after
		{
			animation-duration: 0s !important;
			animation-delay: 0s !important;
		}
	}

	@media screen and (max-width: 640px)
	{
		html
		{
			font-size: 12px;
		}
	}
</style>
