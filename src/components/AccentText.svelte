<span class="accent-text"><slot></slot></span>

<style>
	.accent-text {
		color: white;
		transition-duration: 0.2s;
		animation: background-pan 20s linear infinite;
		background: linear-gradient(
			to right,
			var(--gradient4),
			var(--gradient5),
			var(--gradient6),
			var(--gradient4)
		);
		-webkit-background-clip: text;
		-webkit-text-fill-color: transparent;
		background-clip: text;
		background-size: 200%;
		white-space: nowrap;
		font-weight: 700;
	}
</style>