<template>
	<layout>
		<header>
			<search-button/>
			<darkmode-button/>
			<noscript>
				<no-script-banner/>
			</noscript>
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
		</main>
	</layout>
</template>

<script>
	import SearchButton from "@/components/SearchButton";
	import DarkmodeButton from "@/components/DarkmodeButton";
	import BookShelf from "@/components/BookShelf";
	import BookSpine from "@/components/BookSpine";
	import NoScriptBanner from '@/components/NoScriptBanner';

	export default 
	{
		components:
		{
			SearchButton,
			DarkmodeButton,
			BookShelf,
			BookSpine,
			NoScriptBanner
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

	@media screen and (max-width: 550px)
	{
		.bookshelf
		{
			transform: scale(0.6);
			transform-origin: top;
		}
	}
</style>
