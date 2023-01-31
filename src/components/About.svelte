<script>
	import AccentText from "./AccentText.svelte";
</script>

<section id="about">
	<div class="flex-row">
			<img src="img/portrait-600.png" class="portrait" alt="Wayne
			Cen Portrait">

		<p class="about-me">
			Graduated with a <AccentText><a
			href="https://design.ampd.yorku.ca/" target="_blank">Bachelor of
			Design</a></AccentText> from York University. Focused mainly on
			<AccentText>UX & UI</AccentText> design, dabbling in coding
			courses. Fell in love with programming. Spent a year building
			projects to learn how to code.
			<AccentText>Passionate</AccentText> about learning, writing, and
			video games. <AccentText>React</AccentText> and
			<AccentText>TypeScript</AccentText> are my frameworks of choice.
			Currently developing demos for my passion project,
			<AccentText>
				<a href="https://lets-code-chi.vercel.app/"
				target="_blank">Let's Code</a></AccentText>, built using <AccentText>Next.js</AccentText>.
			<br>
			<br>
			Available for <AccentText>front-end developer</AccentText> roles. 
		</p>
	</div>
</section>

<style>
	.flex-row {
		display: flex;
		gap: 48px;
	}
	
	.portrait {
		width: 320px;
		height: 200px;
		border-radius: 4px;
	}

	.about-me {
		font-family: var(--primary);
		font-weight: 600;
		font-size: 1.4rem;
		color: var(--grey);
		max-width: var(--paragraph-length);
		line-height: 2.4rem;
		margin-top: -8px;
	}

	a:hover {
		color: white;
		text-decoration: underline;
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

	@media screen and (max-width: 1440px) {
		section {
			--sidePadding: 6%;
		}
	}

	@media screen and (max-width: 810px) {
		.about-me {
			font-size: 1rem;
			line-height: 2rem;
		}

		.portrait {
			height: 180px;
		}
	}

	@media screen and (max-width: 720px) {
		.portrait {
			width: 100%;
			height: auto;
		}

		.flex-row {
			flex-direction: column;
		}
	}
	
</style>