<h2 class="subHeader"><slot></slot></h2>

<style>
	.subHeader {
		margin-left: var(--sidePadding);
		margin-bottom: 16px;
		color: var(--grey);
		font-size: 1rem;
		font-weight: 600;
	}
	
	@media screen and (max-width: 1440px) {
		.subHeader {
			--sidePadding: 6%;
		}
	}
</style>