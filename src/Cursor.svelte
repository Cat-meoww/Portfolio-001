<script>
	import { onMount } from "svelte";

	let m = { x: 0, y: 0 };
	let mouseCursor;
	let clicked = false;
	let isHovered = false;

	onMount(() => {
		const links = document.querySelectorAll("a");
		links.forEach((link) => {
			link.addEventListener("mouseleave", () => {
				isHovered = false;
			});
			link.addEventListener("mouseenter", () => {
				isHovered = true;
			});
		});
	});

	function handleMousemove(event) {
		m.x = event.clientX;
		m.y = event.clientY;
		mouseCursor.style.left = m.x + "px";
		mouseCursor.style.top = m.y + "px";
	}

	function handleMousedown() {
		clicked = true;
	}

	function handleMouseup() {
		clicked = false;
	}
</script>

<svelte:body
	on:mousemove={handleMousemove}
	on:mousedown={handleMousedown}
	on:mouseup={handleMouseup} />

<div
	bind:this={mouseCursor}
	class={isHovered ? "innerdot link-hover" : "innerdot"}
	class:active={clicked}
/>

<style>
	.innerdot {
		opacity: 1;
		width: 13px;
		height: 13px;
		background: var(--cursor-color);
		border-radius: 50%;
		position: fixed;
		pointer-events: none;
		transform: translate(-50%, -50%);
		transform-origin: 75% 75%;
		transition: background 0.1s cubic-bezier(0, 0.39, 0.7, 1);
		transition-property: width, height, transform;
		transition-duration: 0.125s;
		z-index: 99;
	}

	.active {
		width: 8px;
		height: 8px;
		transition: all 0.1s ease-out;
	}

	.link-hover {
		border: 1px rgba(250, 250, 250, 0.5) solid;
		background: var(--cursor-hover);
		transform: scale(2.5);
		transition: 0.1s cubic-bezier(0, 0.39, 0.7, 1);
		transition-property: transform;
	}

	@media screen and (max-width: 810px) {
		.innerdot {
			display: none;
		}
	}
</style>
