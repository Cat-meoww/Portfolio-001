<script>
	import About from "./components/About.svelte";
	import Divider from "./components/Divider.svelte";
	import Footer from "./components/Footer.svelte";
	import NavBar from "./components/NavBar.svelte";
	import Project from "./components/Project.svelte";
	import Subheader from "./components/Subheader.svelte";
	import Writing from "./components/Writing.svelte";
	import Cursor from "./Cursor.svelte";
</script>

<main>
	<Cursor />
	<NavBar/>
	<section class="overview">
		<h1 class="header">
			I'm Wayne Cen <img
				src="/img/hand-wave-emoji.png"
				class="emoji--handwave"
				alt="Hand wave emoji"
			/>
		</h1>
		<p class="description">
			Software developer and designer — specializing in designing and
			building accessible, fun, and <span class="magic">eye-catching</span> things
			for the web.
		</p>
	</section>
	<Divider />
	<Subheader>Selected Work</Subheader>
	<section class="projects">
		<Project name="Tenzi" link="https://tenzi-game.vercel.app/"
		token="React"
			><p>
				A game of rolling dice quickly until you hold ten dice of equal value
			</p>
		</Project>
		<Project name="Quizzical" link="https://quizzical-ten.vercel.app/" token="React"
			><p>Multiple choice trivia game</p></Project
		>
		<Project name="The Weather"
		link="https://the-weather-six.vercel.app/" token="HTML, CSS, JS"
			><p>
				Search the weekly weather forecast for any location
			</p>
		</Project>
	</section>
	<Divider />
	<Subheader>About Me</Subheader>
	<About/>
	<Divider />
	<Subheader>Writing</Subheader>
	<Writing/>
	<Divider />
	<Footer />
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
		flex-direction: row;
		justify-content: space-between;
	}

	/* accent text */
	@keyframes background-pan {
		from {
			background-position: 0% center;
		}

		to {
			background-position: -200% center;
		}
	}

	p > .magic {
		animation: background-pan 5s linear infinite;
		background: linear-gradient(
			to right,
			var(--gradient1),
			var(--gradient2),
			var(--gradient3),
			var(--gradient1)
		);
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		background-clip: text;
		background-size: 200%;
		white-space: nowrap;
		font-weight: 700;
		font-size: 1rem;
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
