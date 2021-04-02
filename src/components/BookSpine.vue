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
	}

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
		}
	}


	.first         { left:   8px;   }
	.first.top     { bottom: 294px; }
	.first.middle  { bottom: 166px; }
	.first.bottom  { bottom: 38px;  }

	.second        { left:   252px; }
	.second.top    { bottom: 282px; }
	.second.middle { bottom: 126px; }
	.second.bottom { bottom: 10px;  }
</style>
