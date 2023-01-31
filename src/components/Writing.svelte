<script>
	export let milestones=[];
	import Subheader from "./Subheader.svelte";
</script>
<div >
	<Subheader>Milestones</Subheader>
<div class="wrapper">
	{#each milestones as {title,date,link}}
	<a
	href={link}
	target="_blank" class="article-link">{title}
	<p class="date"> {date}</p>
	</a>
	{/each}
	
	
	
</div>
</div>

<style>
	a:hover {
		color: var(--linkHover);
	}

	.wrapper {
		display: flex;
		flex-direction: column;
		margin-bottom: 32px;
		padding: 0px var(--sidePadding);
	}

	.article-link {
		font-weight: 700;
		border-bottom: 1px var(--divider) solid;
		padding: 32px 0px;
	}

	.date {
		margin-top: 4px;
		font-weight: 300;
		font-size: 0.9rem;
		color: var(--grey);
	}

	@media screen and (max-width: 1440px) {
		.wrapper {
			--sidePadding: 6%;
		}

		.article-link {
		padding: 16px 0px;
		}
	}
</style>