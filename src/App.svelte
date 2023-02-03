<script>
	import About from "./components/About.svelte";
	import Divider from "./components/Divider.svelte";
	import Footer from "./components/Footer.svelte";
	import NavBar from "./components/NavBar.svelte";
	import Project from "./components/Project.svelte";
	import Subheader from "./components/Subheader.svelte";
	import Writing from "./components/Writing.svelte";
	import Cursor from "./components/Cursor.svelte";
	import Skills from "./components/Skills.svelte";
	import {data} from "./lib/data.js";
</script>
<svelte:head>
	<title>{data.name}</title>
</svelte:head>
<main>
	<Cursor />
	<NavBar/>
	<section class="overview">
		<h1 class="header">
			I'm {data.name} <img
				src="/img/hand-wave-emoji.png"
				class="emoji--handwave"
				alt="Hand wave emoji"
			/>
		</h1>
		<p class="description">
		{@html data.description}
		</p>
	</section>
	<Divider />
	<Subheader>Previous Works</Subheader>
	<section class="projects">
		{#each data.projects as project }
		   <Project {...project} />
		{/each}	
	</section>
	<Divider id="about"/>
        <About/>
	<Divider />
		<Skills skills={data.skills} />
	<Divider />
	   <Writing milestones={data.milestones}/>
	<Divider />
		<Footer socials={data.socials} mailid={data.mailid}/>
	<Divider />
</main>

<style>
	:global(body) {
		background-color: var(--bg-dark);
		color: var(--text-offwhite);
	}

	:global(section) {
		margin: 0 var(--sidePadding);
	}

	/* Util */
	.overview {
		margin-top: 10vmin;
	}

	main {
		display: flex;
		flex-direction: column;
		font-family: var(--primary);
	}

	.header {
		font-family: var(--primary);
		font-size: 1.6rem;
		font-weight: 600;
		margin-bottom: 8px;
	}

	.description {
		font-size: 1rem;
		font-weight: 400;
		max-width: var(--paragraph-length);
		line-height: 1.5rem;
		margin-bottom: 20px;
		color: var(--grey);
	}

	/* Projects */
	.projects {
		display: flex;
		flex-wrap: wrap;
		row-gap: 20px;
		flex-direction: row;
		justify-content: space-between;
	}


	/* CSS Animations */
	@keyframes handwave {
		from {
			transform: rotate(0deg);
		}
		50% {
			transform: rotate(45deg);
		}
		to {
			transform: rotate(0deg);
		}
	}

	.emoji--handwave {
		width: 24px;
		transition: transform 0.3s ease-out;
	}

	.emoji--handwave:hover {
		animation: handwave 0.4s linear infinite;
	}

	/* Laptop */
	@media screen and (max-width: 1440px) {
		section {
			--sidePadding: 6%;
		}
	}

	/* Tablet */
	@media screen and (max-width: 810px) {
		.projects {
			width: 90%;
		}
	}

	/* Mobile */
	@media screen and (max-width: 720px) {
		main {
			overflow-x: hidden;
		}

		section {
			--sidePadding: 6%;
		}

		.projects {
			flex-direction: column;
		}
	}
</style>
