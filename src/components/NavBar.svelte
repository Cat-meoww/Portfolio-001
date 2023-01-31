<nav>
	<a href="/">
		<img src="img/favicon.ico" class="logo" alt="Logo icon" />
	</a>
	<div class="linkWrapper">
		<a href="#about">About</a>
		<div class="linkDivider">|</div>
		<a
			href="https://drive.google.com/file/d/1Xcp28qiHAozYg7DSoIP8xLjTqj0Zzo-E/view?usp=sharing"
			target="_blank">
			Resume
		</a>
	</div>
</nav>

<style>
		nav {
		display: flex;
		justify-content: space-between;
		background: rgba(0, 0, 0, 0.5);
		padding: 16px var(--sidePadding);
		font-size: 0.9rem;
		position: sticky;
		top: 0;
		z-index: 98;
		-webkit-backdrop-filter: blur(8px) brightness(200%) opacity(90%);
		backdrop-filter: blur(8px) brightness(200%) opacity(90%);
	}

	.logo {
		display: flex;
		width: var(--logoSize);
		height: var(--logoSize);
		transition: transform 1s ease-in-out;
	}

	.logo:hover {
		transform: scale(1.15) rotate3d(1, 1, 1, 360deg);
	}

	.linkWrapper {
		display: flex;
		font-weight: 600;
		gap: 16px;
	}

	.linkWrapper a:hover {
		color: var(--linkHover);
	}

	.linkDivider {
		color: var(--divider);
		font-weight: 600;
	}

	@media screen and (max-width: 1440px) {
		nav {
			--sidePadding: 6%;
		}
	}
</style>