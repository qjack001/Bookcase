<template>
	<section>
		<svg :class="{ 'no-animate': noAnimate }" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 496 422" role="figure" aria-label="Book shelves">
			<g class="first-case">
				<path class="bookshelf-background" d="M0 0h240v384H0zM246"/>
				<g class="bookshelf-sides">
					<path stroke="none" d="M0 0h8v422H0z"/>
					<path fill="none" d="M.5.5h7v421h-7z"/>
					<path stroke="none" d="M7 0h226v8H7z"/>
					<path fill="none" d="M7.5.5h225v7H7.5z"/>
					<path stroke="none" d="M7 384h226v8H7z"/>
					<path fill="none" d="M7.5 384.5h225v7H7.5z"/>
					<path stroke="none" d="M7 391h226v31H7z"/>
					<path fill="none" d="M7.5 391.5h225v30H7.5z"/>
					<path stroke="none" d="M7 256h226v8H7z"/>
					<path fill="none" d="M7.5 256.5h225v7H7.5z"/>
					<path stroke="none" d="M7 128h226v8H7z"/>
					<path fill="none" d="M7.5 128.5h225v7H7.5z"/>
					<path stroke="none" d="M232 0h8v422h-8z"/>
					<path fill="none" d="M232.5.5h7v421h-7z"/>
				</g>
			</g>
			<g class="second-case">
				<path class="bookshelf-background" d="M246 55h248v362H246z"/>
				<g class="bookshelf-sides">
					<path stroke="none" d="M244 52h8v370h-8z"/>
					<path fill="none" d="M244.5 52.5h7v369h-7z"/>
					<path stroke="none" d="M488 52h8v370h-8z"/>
					<path fill="none" d="M488.5 52.5h7v369h-7z"/>
					<path stroke="none" d="M251 412h238v8H251z"/>
					<path fill="none" d="M251.5 412.5h237v7h-237z"/>
					<path stroke="none" d="M251 296h238v8H251z"/>
					<path fill="none" d="M251.5 296.5h237v7h-237z"/>
					<path stroke="none" d="M251 140h238v8H251z"/>
					<path fill="none" d="M251.5 140.5h237v7h-237z"/>
					<path stroke="none" d="M251 52h238v8H251z"/>
					<path fill="none" d="M251.5 52.5h237v7h-237z"/>
				</g>
			</g>
		</svg>
		<slot/>
	</section>
</template>

<script>
	export default 
	{
		props: [ "noAnimate" ]
	};
</script>

<style scoped>
	.bookshelf-background
	{
		fill: var(--grey-30);
	}

	.bookshelf-sides
	{
		fill: var(--grey-20);
		stroke: var(--grey-10);
	}

	section
	{
		position: relative;
		box-sizing: border-box;
		width: 496px;
		height: 422px;
	}
</style>
