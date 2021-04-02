<template>
	<li :class="{ 'no-animate': noAnimate }" 
		:style="{ animationDelay: animationDelay + 's' }">
		{{ tag }}
	</li>
</template>

<script>
	export default
	{
		props: [ 
			"tag", 
			"animationDelay", 
			"noAnimate" 
		]
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

		animation: rise-up 0.8s cubic-bezier(0,1.4,.6,1),
				fade-in 0.8s ease;
		animation-fill-mode: forwards;
		opacity: 0;
	}

	li.no-animate
	{
		animation: none;
		opacity: 1;
	}

	@keyframes rise-up
	{
		from { transform: translateY(50px); }
		to { transform: translateY(0px); }
	}

	@keyframes fade-in
	{
		from { opacity: 0; }
		to { opacity: 1; }
	}

	@media screen and (max-width: 640px)
	{
		section li
		{
			font-size: 0.95em;
		}
	}
</style>
