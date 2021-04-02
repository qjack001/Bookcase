<template>
	<layout>
		<header>
			<span></span>
			<darkmode-button/>
		</header>
		<ul class="book-list">
			<book-list-item 
				:key="book.node.id" 
				v-for="book in books" 
				:post="book.node" />
		</ul>
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
		metaInfo:
		{
			title: "Bookcase"
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
