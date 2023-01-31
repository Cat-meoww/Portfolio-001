<section>
	<footer>
		<p class="contact">
			Let's work together
			<span class="email">
				<a href="mailto:wayne.cen@gmail.com" class="email"> wayne.cen@gmail.com </a>
			</span>
		</p>
		<div class="wrapper">
			<a class="socials" href="https://medium.com/@wayne.cen" target="_blank">
				<p>Medium</p>
			</a>
			<a
				class="socials"
				href="https://www.linkedin.com/in/waynercen/"
				target="_blank"
			>
				<p>LinkedIn</p>
			</a>
			<a class="socials" href="https://github.com/waynecen" target="_blank">
				<p>GitHub</p>
			</a>
			<a
				class="socials"
				href="https://www.instagram.com/waynercen/"
				target="_blank"
			>
				<p>Instagram</p>
			</a>
		</div>
	</footer>
</section>

<style>
	footer {
		display: flex;
		justify-content: space-between;
		font-size: 0.9rem;
		font-weight: 600;
	}

	.contact {
		color: var(--grey);
	}

	.socials {
		opacity: 0.6;
		height: fit-content;
	}

	.socials:hover {
		opacity: 1;
		color: var(--linkHover);
	}

	.email {
		display: flex;
		flex-direction: column;
		font-size: 1.2rem;
		font-weight: 600;
		transition: color 0.225s ease-out;
		color: white;
	}

	.email a:hover {
		color: var(--linkHover);
	}

	.wrapper {
		display: flex;
		flex-direction: row;
	}

	.wrapper a {
		padding: 8px;
		margin-left: 8px;
	}

	@media screen and (max-width: 1440px) {
		section {
			--sidePadding: 6%;
		}

		.email {
			font-size: 1rem;
		}
	}

	@media screen and (max-width: 720px) {
		.contact {
			display: none;
		}
	}
</style>
