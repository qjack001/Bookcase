<template>
	<layout>
		<header>
			<search-button/>
			<darkmode-button/>
		</header>
		<main>
			<book-shelf :noAnimate="true" class="bookshelf">
				<book-spine
					:key="book.node.id" 
					v-for="book in books"

					:title="book.node.title"
					:shelf="book.node.shelf"
					:bookcase="book.node.bookcase"
					:distance="book.node.distance"
					:width="book.node.width"
					:height="book.node.height"
					:background="book.node.background"
					:noAnimate="true"
				/>
			</book-shelf>
			<h1>??</h1>
			<p>
				Since working on Bookplate, I've been interested in the record-keeping and
				archival of my own personal library. While Bookplate offers data organized
				by status (read, not-read, want-to-read, etc.), this site considers it from
				a more phisical perspective. Bookshelves are an often overlooked interface
				for catagorization. The spacial relations naturally created between books,
				both intentional and incidental, provide a depth of information without any
				additional elements.
			</p>
			<p>
				Unfortunatly, this sorting method makes actually finding the book you're
				looking for kind of difficult. This site is a map of where my books are, 
				and a digital archive of their arrangment.
			</p>
			<p>
				While my library is fairly small, I think it provides a proof-of-concept
				for the idea on a larger scale. My initial (not very practical) design
				included an RFID system (chips imbedded into the books, recievers in the 
				shelves) for tracking the placment automatically. An LED strip would then
				line the backs of the shelves, and iluminate the selected book IRL.
			</p>
		</main>
	</layout>
</template>

<script>
	import SearchButton from "@/components/SearchButton";
	import DarkmodeButton from "@/components/DarkmodeButton";
	import BookShelf from "@/components/BookShelf";
	import BookSpine from "@/components/BookSpine";

	export default 
	{
		components:
		{
			SearchButton,
			DarkmodeButton,
			BookShelf,
			BookSpine
		},
		metaInfo() 
		{
			return {
				title: 'About',
			};
		},
		computed:
		{
			books() 
			{
				return this.$page.allPost.edges;
			}
		}
	};
</script>

<page-query>
	query
	{
		allPost(filter: { date: { gte: "2020" }})
		{
			totalCount
			edges
			{
				node
				{
					id
					title
					
					bookcase
					shelf
					distance
					width
					height
					background

					path
				}
			}
		}
	}
</page-query>

<style scoped>
	header
	{
		display: grid;
		grid-template-columns: auto auto;
	}

	.bookshelf
	{
		margin: 100px auto 0;
	}

	h1
	{
		margin-top: 60px;
		font-size: var(--lg-text);
		font-weight: normal;
		font-style: italic;
		letter-spacing: -0.02em;
		line-height: 1;
		text-align: center;

		overflow-wrap: break-word;
		word-wrap: break-word;
		hyphens: auto;
	}

	p
	{
		max-width: 60ch;
		margin: 0 auto;
		padding: 0 20px;

		font-size: var(--md-text);
		text-align: justify;
		text-indent: 40px;

		overflow-wrap: break-word;
		word-wrap: break-word;
		hyphens: auto;
	}

	@media screen and (max-width: 550px)
	{
		.bookshelf
		{
			transform: scale(0.6);
			transform-origin: top;
		}

		h1
		{
			margin-top: -120px;
		}
	}
</style>
