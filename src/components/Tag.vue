<template>
	<li>
		{{ this.tag }}
	</li>
</template>

<script>
	export default
	{
		props: ["tag"]
	};
</script>

<style scoped>
	li
	{
		display: inline-block;
		list-style: none;
		margin: 2.5px 2px;
		padding: 2px 4px;

		color: var(--grey-10);
		font-size: var(--sm-text);
		font-style: normal;
		text-transform: uppercase;
		letter-spacing: 0.065em;

		background: var(--grey-50);
		border: 1px solid var(--grey-20);
		border-radius: 4px;
	}

	@media screen and (max-width: 640px)
	{
		section li
		{
			font-size: 0.95em;
		}
	}
</style>
