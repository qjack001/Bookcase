<template>
	<form>
		<svg class="icon" role="presentation" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 38.537 34.109">
			<path d="M4.02 16.141a10 10 0 0119.405-4.838 9.926 9.926 0 01-.584 6.526l11.151 6.7-1.212 2.017-11.15-6.7a10 10 0 01-13.058 2.448 9.935 9.935 0 01-4.553-6.153zm7.852-9.838a7.647 7.647 0 103.7 14.839 7.647 7.647 0 10-3.7-14.84z"/>
		</svg>
		<input 
			type="search" 
			placeholder="Search" 
			id="search-bar"
			:value="value"
			v-on:input="updateValue($event.target.value)"
		/>
		<label for="search-bar">Search</label>
	</form>
</template>

<script>
	export default 
	{
		props: [ "value" ],
		mounted()
		{
			document.getElementById('search-bar').focus();
		},
		methods:
		{
			updateValue: function (value)
			{
				this.$emit('input', value)
			}
		}
	};
</script>

<style scoped>
	form
	{
		position: relative;
		display: grid;
		grid-template-columns: 3rem auto;
		grid-template-rows: 3rem;
		height: 3rem;

		box-sizing: border-box;
		padding: 20px 30px;

		text-decoration: none;
		color: var(--grey-10);
	}

	.icon
	{
		fill: currentColor;
		width: 2.5rem;
		margin-top: 0.5rem;
	}

	input
	{
		font-family: 'Times New Roman', Times, serif;
		color: var(--grey-00);
		font-size: var(--md-text);
		font-style: italic;
		line-height: 3rem;
		letter-spacing: 0.025em;

		outline: none;
		border: none;
		background: transparent;
	}

	input:focus
	{
		border-bottom: 1px solid var(--grey-10);
	}
	
	label
	{
		display: block;
		width: 0px;
		height: 0px;
		opacity: 0;
		pointer-events: none;
	}
</style>
