<script>
	export let name, link, token;
</script>

<div class="card">
	<a href={link} target="_blank">
		<div class="card-content">
			<div class="wrapper">
				<h3 class="card-title">{name}</h3>
				<h4 class="card-subtitle"><slot></slot></h4>
			</div>
			<div class="token">{token}</div>
		</div>
	</a>
</div>

<style>
	.card {
		aspect-ratio: 1.6 / 1;
		border: 0.2vmin solid var(--border);
		cursor: none;
		position: relative;
		width: var(--cardSize);
		border-radius: 4px;
	}

	.card:hover:before {
		background-position: 100% 100%;
		transform: scale(1.08, 1.08);
	}

	.card:before {
		background: linear-gradient(
			130deg,
			transparent 0% 33%,
			var(--gradient1) 66%,
			var(--gradient2) 83.5%,
			var(--gradient3) 100%
		);
		background-position: 0% 0%;
		background-size: 300% 300%;
		content: "";
		height: 100%;
		left: 0px;
		position: absolute;
		top: 0px;
		transition: all 350ms ease;
		width: 100%;
		filter: brightness(0.9);
		border-radius: 2px;
	}

	.card-content {
		background-image: radial-gradient(
			rgba(255, 255, 255, 0.2) 8%,
			transparent 8%
		);
		background-position: 0% 0%;
		background-size: 3vmin 3vmin;
		height: calc(100% - 4vmin);
		padding: 2vmin;
		position: relative;
		transition: background-position 350ms ease;
		width: calc(100% - 5vmin);
		display: flex;
		flex-direction: column;
		justify-content: space-between;
	}

	.card-title,
	.card-subtitle {
		color: white;
		font-weight: 400;
		margin: 0px;
	}

	.card-title {
		font-size: 2.2vmin;
		font-weight: 600;
	}

	.card-subtitle {
		font-family: var(--primary);
		font-size: 0.9rem;
		font-weight: 400;
		margin-top: 1vmin;
		margin-bottom: 0vmin;
	}

	.token {
		padding: 1vmin 1.2vmin;
		background-color:rgba(255, 255, 255, 0.2);
		border-radius: 1.6vmin;
		width: fit-content;
		font-size: 1.4vmin;
		font-weight: 600;
	}

	@media screen and (max-width: 810px) {
		.card {
			aspect-ratio: 1.2 / 1;
		}

		.card-subtitle {
			margin-bottom: 8px;
		}
	}

	@media screen and (max-width: 720px) {
		.card {
			aspect-ratio: 1.6 / 1;
			width: 100%;
			margin-bottom: 32px;
		}

		.card-title {
			font-size: 5.6vmin;
		}

		.token {
			font-size: 3.2vmin;
		}
	}
</style>
