<template>
	<layout>
		<header>
			<search-button/>
			<darkmode-button/>
		</header>
		<main>
			<section>
				<h1>{{ $page.post.title }}</h1>
				<p>{{ $page.post.author }}</p>
				<article v-html="$page.post.content"/>
				<ul class="keywords" aria-label="keywords">
					<tag :key="tag" 
						v-for="(tag, index) in $page.post.tags" 
						:tag="tag"
						:animationDelay="(index / 10) + 0.4"
					/>
				</ul>
			</section>
			<book-shelf class="bookshelf">
				<book-spine 
					:shelf="$page.post.shelf" 
					:bookcase="$page.post.bookcase" 
					:distance="$page.post.distance" 

					:width="$page.post.width"
					:height="$page.post.height"

					:title="$page.post.title"
					:background="$page.post.background"
				/>
			</book-shelf>
		</main>
	</layout>
</template>

<script>
	import SearchButton from '@/components/SearchButton';
	import DarkmodeButton from '@/components/DarkmodeButton';
	import Tag from '@/components/Tag';
	import BookShelf from '@/components/BookShelf';
	import BookSpine from '@/components/BookSpine';

	export default
	{
		components:
		{
			SearchButton,
			DarkmodeButton,
			Tag,
			BookShelf,
			BookSpine
		},
		metaInfo() 
		{
			return {
				title: this.$page.post.title,
			};
		}
	}
</script>

<page-query>
	query Post ($path: String!)
	{
		metadata
		{
			siteName
			siteDescription
		}
		post: post (path: $path)
		{
			id
			date (format: "D MMMM YYYY")

			title
			author
			content
			tags

			bookcase
			shelf
			distance
			width
			height
			background
		}
	}
</page-query>

<style scoped>
	header
	{
		display: grid;
		grid-template-columns: auto auto;
	}

	main
	{
		margin: 100px auto;
		display: grid;
		grid-template-columns: 560px 496px;
		width: 1121px;
		gap: 80px;
	}
	
	h1,
	p,
	article
	{
		animation: fade-in 0.4s ease-in;
		animation-fill-mode: forwards;
		opacity: 0;
	}

	h1
	{
		margin-top: 1.5em;
		font-size: var(--lg-text);
		font-weight: normal;
		font-style: italic;
		letter-spacing: -0.02em;
		line-height: 1;

		overflow-wrap: break-word;
		word-wrap: break-word;
		hyphens: auto;

		animation-duration: 0.6s;
	}

	p, 
	article
	{
		font-size: var(--md-text);
		padding-left: 100px;

		overflow-wrap: break-word;
		word-wrap: break-word;
		hyphens: auto;

		animation-delay: 0.2s;
	}

	article
	{
		text-indent: 40px;
		animation-delay: 0.3s;
	}

	ul
	{
		padding-left: 95px; /* 100px, subtract margin from tags */
	}

	@keyframes fade-in
	{
		from { opacity: 0; }
		to { opacity: 1; }
	}

	@media screen and (max-width: 1200px)
	{
		main
		{
			grid-template-columns: 555px 372px;
			width: 967px;
			gap: 40px;
		}

		.bookshelf
		{
			transform: scale(0.75);
			transform-origin: left;
		}
	}

	@media screen and (max-width: 1000px)
	{
		main
		{
			margin: 0px auto;
			margin-top: -40px;
			grid-template-columns: 100%;
			gap: 0px;
			
			width: 100%;
			box-sizing: border-box;
			padding: 40px;
			padding-top: 0;
		}

		.bookshelf
		{
			grid-row: 1;
			transform-origin: right bottom;
			justify-self: right;
		}

		h1
		{
			margin-top: 0.5em;
		}

		p, 
		article
		{
			padding-left: 80px;
			max-width: 500px;
		}

		ul
		{
			padding-left: 75px; /* 100px, subtract margin from tags */
		}
	}

	@media screen and (max-width: 640px)
	{
		main
		{
			padding: 0 20px 40px;
		}
	}

	@media screen and (max-width: 530px)
	{
		main
		{
			grid-template-rows: 300px auto;
		}

		h1
		{
			margin-top: 1em;
		}

		.bookshelf
		{
			transform: scale(0.5) translateY(-250px);
		}

		p, 
		article,
		ul
		{
			padding-left: 0px;
		}
	}
</style>
