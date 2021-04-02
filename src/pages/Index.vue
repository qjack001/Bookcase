<template>
	<layout>
		<header>
			<span></span>
			<darkmode-button/>
		</header>
		<nav>
			<ul class="book-list" aria-label="books">
				<book-list-item 
					:key="book.node.id" 
					v-for="book in books" 
					:post="book.node" 
				/>
			</ul>
		</nav>
	</layout>
</template>

<script>
	import DarkmodeButton from "@/components/DarkmodeButton";
	import BookListItem from "@/components/BookListItem";

	export default 
	{
		components:
		{
			DarkmodeButton,
			BookListItem
		},
		metaInfo() 
		{
			return {
				title: 'Home',
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
		metadata
		{
			siteName
			siteDescription
		}
		allPost(filter: { date: { gte: "2020" }})
		{
			totalCount
			edges
			{
				node
				{
					id
					title
					author
					tags
					date (format: "MMM D YYYY")
					path
				}
			}
		}
	}
</page-query>

<style>
	ul
	{
		margin-top: 40px;
		padding: 0;
	}
</style>
