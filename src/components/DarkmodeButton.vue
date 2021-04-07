<template>
	<div class="darkmode-button">
		<input 
			type="checkbox" 
			id="darkmode-toggle" 
			@change="toggleDarkmode()" 
			v-on:keyup.enter="enterOverride()"
		/>
		<label for="darkmode-toggle">Darkmode</label>
		<div id="darkmode-mask" role="presentation"></div>
	</div>
</template>

<script>
	export default 
	{
		methods:
		{
			toggleDarkmode()
			{
				document.getElementById("darkmode-mask").className = "hide";
				setTimeout(function () {
					document.body.classList.toggle("darkmode");
					document.getElementById("darkmode-mask").className = "";
    			}, 600);
			},

			enterOverride()
			{
				let checkbox = document.getElementById('darkmode-toggle');
				checkbox.checked = !checkbox.checked;
				this.toggleDarkmode();
			}
		}
	};
</script>

<style scoped>
	.darkmode-button
	{
		position: relative;
		height: 3rem;
		box-sizing: border-box;
		padding: 20px 40px;
		text-align: right;
	}

	input, 
	label
	{
		cursor: pointer;
		position: relative;
		padding-right: calc(1.5 * var(--md-text));

		color: var(--grey-10);
		font-family: 'Times New Roman', Times, serif;
		font-style: italic;
		font-size: var(--md-text);
		letter-spacing: 0.025em;
		line-height: 3rem;
	}

	input
	{
		opacity: 0;
	}

	label::before,
	label::after
	{
		content: "";
		display: block;
		position: absolute;
		top: 0px;
		right: 0px;

		width: var(--md-text);
		height: var(--md-text);
		border-radius: 100%;

		background: var(--grey-10);
	}

	label::after
	{
		transform: scale(0.7) translateX(25px) translateY(-25px);
		transition: transform 2s ease;
		background: var(--grey-40);
	}

	.darkmode label::after
	{
		transform: scale(0.7) translateX(0.6rem) translateY(-0.6rem);
	}

	[v-focus-visible=true] .darkmode-button:focus-within::after
	{
		content: "";
		display: block;
		position: absolute;
		top: 10px;
		right: 20px;
		width: 23ch;
		height: 4.2rem;

		border: 2px solid var(--grey-10);
		border-radius: 4px;

		pointer-events: none;
	}

	.darkmode-button:hover label,
	[v-focus-visible=true] .darkmode-button:focus-within label
	{
		color: var(--grey-00);
	}

	.darkmode-button:hover label::before,
	[v-focus-visible=true] .darkmode-button:focus-within label::before
	{
		background: var(--grey-00);
	}

	#darkmode-mask
	{
		z-index: 999;
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;

		background-color: #000;
		pointer-events: none;

		opacity: 0;
		transition: opacity 1s ease-out;
	}

	#darkmode-mask.hide
	{
		opacity: 1;
		transition: opacity 0.6s ease-in;
	}

	@media (prefers-reduced-motion)
	{
		#darkmode-mask
		{
			display: none;
		}
	}
</style>
