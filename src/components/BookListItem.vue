<template>
	<li class="book-item">
		<g-link :to="post.path">
			{{ post.title }}
			<span class="author">
				— {{ post.author }}
			</span>
			<ul class="keywords">
				<title>Keywords</title>
				<tag :key="tag" 
					v-for="tag in post.tags" 
					:tag="tag"
					:noAnimate="true"
				/>
			</ul>
		</g-link>
	</li>
</template>

<script>
	import Tag from '@/components/Tag';

	export default
	{
		props: [ "post" ],

		components:
		{
			Tag
		}
	};
</script>

<style scoped>
	.book-item
	{
		list-style: none;
		margin: 5px 20px;
		box-sizing: border-box;
		background: var(--grey-50);

		position: relative;
	}

	.book-item > a
	{
		display: block;
		width: 100%;
		box-sizing: border-box;
		padding: 0 20px;
		border: solid 1px var(--grey-50);

		color: var(--grey-00);
		font-size: var(--md-text);
		text-decoration: none;
		font-style: italic;
		line-height: 3.75rem;

		/* to stop the tags from overflowing */
		white-space: nowrap;
		overflow: scroll hidden;
	}

	.book-item::after
	{
		content: "";
		display: block;
		position: absolute;
		top: 1px;
		right: 1px;
		bottom: 1px;
		width: 40px;

		pointer-events: none;
  		background: linear-gradient(
			to right,
			hsla(0, 0%, 100%, 0.000) 0.00%,
			hsla(0, 0%, 100%, 0.013) 8.90%,
			hsla(0, 0%, 100%, 0.049) 16.8%,
			hsla(0, 0%, 100%, 0.104) 23.8%,
			hsla(0, 0%, 100%, 0.175) 30.3%,
			hsla(0, 0%, 100%, 0.259) 36.1%,
			hsla(0, 0%, 100%, 0.352) 41.7%,
			hsla(0, 0%, 100%, 0.450) 47.0%,
			hsla(0, 0%, 100%, 0.550) 52.3%,
			hsla(0, 0%, 100%, 0.648) 57.6%,
			hsla(0, 0%, 100%, 0.741) 63.2%,
			hsla(0, 0%, 100%, 0.825) 69.2%,
			hsla(0, 0%, 100%, 0.896) 75.7%,
			hsla(0, 0%, 100%, 0.951) 82.9%,
			hsla(0, 0%, 100%, 0.987) 90.9%,
			hsl(0, 0%, 100%) 100%); /* --grey-50 */
	}

	/* NOTE: must be manually edited if color palette changes */
	.darkmode .book-item::after
	{
  		background: linear-gradient(
			to right,
			hsla(0, 0%, 16%, 0.000) 0.00%,
			hsla(0, 0%, 16%, 0.013) 8.90%,
			hsla(0, 0%, 16%, 0.049) 16.8%,
			hsla(0, 0%, 16%, 0.104) 23.8%,
			hsla(0, 0%, 16%, 0.175) 30.3%,
			hsla(0, 0%, 16%, 0.259) 36.1%,
			hsla(0, 0%, 16%, 0.352) 41.7%,
			hsla(0, 0%, 16%, 0.450) 47.0%,
			hsla(0, 0%, 16%, 0.550) 52.3%,
			hsla(0, 0%, 16%, 0.648) 57.6%,
			hsla(0, 0%, 16%, 0.741) 63.2%,
			hsla(0, 0%, 16%, 0.825) 69.2%,
			hsla(0, 0%, 16%, 0.896) 75.7%,
			hsla(0, 0%, 16%, 0.951) 82.9%,
			hsla(0, 0%, 16%, 0.987) 90.9%,
			hsl(0, 0%, 16%) 100%); /* --grey-50 */
	}

	a:hover, a:focus
	{
		border-color: var(--grey-00);
	}

	a:focus-visible
	{
		outline-color: var(--grey-10);
	}

	.author
	{
		font-style: normal;
		text-transform: uppercase;
		font-size: 0.95em;
	}

	.keywords
	{
		display: inline-block;
		padding: 0;
		margin: 0;
		margin-left: 20px;

		white-space: nowrap;
		overflow: hidden;

		line-height: 1.2;
		transform: translateY(-4px); /* adjust for safari */
	}

	/* 
	 *	FIXME: super hacky solution to chrome/safari
	 *	rendering the vertical position differently
	 */
	@supports (aspect-ratio: 1 / 1)
	{
		.keywords
		{
			transform: translateY(4px); /* adjust for chrome */
		}
	}

	@media screen and (max-width: 600px)
	{
		.book-item
		{
			margin: 10px;
		}
	}
</style>
