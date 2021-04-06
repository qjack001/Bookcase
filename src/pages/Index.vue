<template>
	<layout>
		<div>
			<noscript>
				<div>
					<no-script-banner/>
				</div>
			</noscript>
		</div>
		<header>
			<search-bar v-model="searchQuery"/>
			<darkmode-button/>
		</header>
		<nav>
			<ul class="book-list" aria-label="books">
				<book-list-item 
					:key="book.node.id" 
					v-for="book in books" 
					:post="book.node"
					v-show="searchMatch(searchQuery, book.node)"
				/>
			</ul>
		</nav>
	</layout>
</template>

<script>
	import DarkmodeButton from "@/components/DarkmodeButton";
	import BookListItem from "@/components/BookListItem";
	import SearchBar from '@/components/SearchBar';
	import NoScriptBanner from '@/components/NoScriptBanner';

	export default 
	{
		data()
		{
			return {
				searchQuery: ''  
			}
		},
		components:
		{
			DarkmodeButton,
			SearchBar,
			BookListItem,
			NoScriptBanner
		},
		metaInfo() 
		{
			return {
				title: 'Search',
			};
		},
		computed:
		{
			books() 
			{
				return this.$page.allPost.edges;
			}
		},
		methods:
		{
			searchMatch(query, book)
			{
				if (query == '') { return true; }

				let infoBlob = [book.title, book.author, book.tags.join(' ')].join(' ').toLowerCase();
				return query.toLowerCase().split(' ').every(e => infoBlob.includes(e))
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
	header
	{
		display: grid;
		grid-template-columns: calc(100vw - 36ch) 36ch;
	}

	ul
	{
		margin-top: 40px;
		padding: 0;
	}
</style>
