<script>
	import AccentText from "./AccentText.svelte";
	import Subheader from "./Subheader.svelte";
</script>

<div >
<Subheader>About Me</Subheader>

<section >
	<div class="flex-row">
			<img src="img/portrait-600.png" class="portrait" alt="Profile Portrait">

		<p class="about-me">
			Graduated with a <AccentText><a
			href="/#" target="_self">Bachelor of
			Degree</a></AccentText> from SV University. Focused mainly on
			<AccentText>Computer sciences and Electronics</AccentText> dabbling in coding
			courses. Fell in love with programming. Spent a year building
			projects to learn how to code.
			<AccentText>Passionate</AccentText> about learning, coding, and
			open sourcing softwares.
			<br><AccentText>Codeigniter and Sveltekit</AccentText> Is my favorite Backend framework.<br>
			<AccentText>Svelte</AccentText> Is my favorite front-end framework of choice.
			<br>
			Efficient knowleged In <AccentText>MYSQL (RDBMS) & MONGODB</AccentText> .<br> 
			<AccentText>Services </AccentText>likes Restapi, Bugfixing, Api Integrations,building core production web apps, static sites are provided.
			<AccentText>
				<!-- svelte-ignore a11y-missing-attribute -->
				<a>Let's built</a></AccentText>, web apps  <AccentText>with Efficient frameworks</AccentText>.
			<br>
			<br>
			Available for <AccentText>Lamp stack developer</AccentText> and <AccentText> JS based platform developer</AccentText> roles. 
		</p>
	</div>
</section>
</div>

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