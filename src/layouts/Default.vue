<template>
	<div>
		<slot/>
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
	}

	body
	{
		background-color: var(--grey-40);
		color: var(--grey-00);

		margin: 0;
		padding: 0;
	}

	header
	{
		margin: 0;
		padding: 0;
	}

	@media screen and (max-width: 640px)
	{
		html
		{
			font-size: 12px;
		}
	}
</style>
