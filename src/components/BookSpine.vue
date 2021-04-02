<template>
	<div
		role="figure" 
		:aria-label="'Book spine, located on the ' + shelf + ' shelf of the ' + bookcase + ' bookcase. The book is ' + distance + ' centimeters from the left-edge of the shelf.'"
		:style="{ width: (width * scaleMultiplier) + 'px', height: (height * scaleMultiplier) + 'px', background: background, transform: 'translateX(' + (distance * scaleMultiplier) + 'px)' }"
		:class="[ bookcase, shelf, { 'no-animate': noAnimate } ]"
	>
	</div>
</template>

<script>
	const MULTIPLIER = 4; // px to cm scale

	export default 
	{
		props: [
			"bookcase",
			"shelf",
			"distance",
			"width",
			"height",
			"background",
			"noAnimate"
		],
		computed:
		{
			scaleMultiplier() 
			{
				return MULTIPLIER;
			}
		}
	};
</script>

<style scoped>
	div
	{
		background: red;
		position: absolute;

		animation: fade-in 0.4s ease;
		opacity: 0;
		animation-fill-mode: forwards;
	}

	div.first { animation-delay: 0.8s; }
	div.second { animation-delay: 1s; }

	@supports (aspect-ratio: 1 / 1)
	{
		div::after
		{
			content: "";
			display: block;

			height: calc(100% + 20px);
			aspect-ratio: 1 / 1;

			margin-top: -10px;
			margin-left: 50%;
			transform: translateX(-50%);

			border: 2px solid;
			border-color: transparent;
			border-radius: 100%;

			animation: spin-circ 1s ease 1s,
					spin-top 0.6s ease 1s,
					spin-right 0.6s ease 1.1s,
					spin-bottom 0.6s ease 1.2s,
					spin-left 0.6s ease-out 1.3s;
		}
	}

	div.no-animate,
	div.no-animate::after
	{
		animation: none;
		opacity: 1;
	}

	.first         { left:   8px;   }
	.first.top     { bottom: 294px; }
	.first.middle  { bottom: 166px; }
	.first.bottom  { bottom: 38px;  }

	.second        { left:   252px; }
	.second.top    { bottom: 282px; }
	.second.middle { bottom: 126px; }
	.second.bottom { bottom: 10px;  }

	@keyframes spin-circ
	{
		0% { transform: translateX(-50%) rotate(0deg); }
		100% { transform: translateX(-50%) rotate(180deg); }
	}

	@keyframes spin-top
	{
		0% { border-top-color: transparent; }
		50% { border-top-color: var(--grey-00); }
		100% { border-top-color: transparent; }
	}

	@keyframes spin-left
	{
		0% { border-left-color: transparent; }
		50% { border-left-color: var(--grey-00); }
		100% { border-left-color: transparent; }
	}

	@keyframes spin-right
	{
		0% { border-right-color: transparent; }
		50% { border-right-color: var(--grey-00); }
		100% { border-right-color: transparent; }
	}

	@keyframes spin-bottom
	{
		0% { border-bottom-color: transparent; }
		50% { border-bottom-color: var(--grey-00); }
		100% { border-bottom-color: transparent; }
	}

	@keyframes fade-in
	{
		from { opacity: 0; }
		to { opacity: 1; }
	}
</style>
