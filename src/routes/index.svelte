<script>
	import Alien from '$lib/Alien.svelte';

	let hovering = false

	let easterEgg = false

	let timer
	function unlock() {
		timer = setTimeout(() => {
			easterEgg = true
		}, 2000)
	}
	function reset() {
		clearTimeout(timer)
	}
	</script>

<div class="button">Don't Click</div>

<div class="container">
	{#each Array(100) as _, i}
		{#if i === 69}
			<div
				class:easterEgg
				class="animation"
				style="animation-delay: -{i}s"
				on:mouseover={() => unlock()}
				on:mouseout={() => reset()}
			/>
		{:else}
			<div class:easterEgg class="animation" style="animation-delay: -{i}s" />
		{/if}
	{/each}

</div>

<Alien {hovering} />

<style>
	.easterEgg {
		background-image: url('https://creators-images.vice.com/content-images/contentimage/no-slug/35f297d210dac499db94bbdfd19e6c04.jpg?resize=640:*');
		background-size: cover;
	}
	h1 {
		text-align: center;
		padding-top: 10vh;
	}
	.thing {
		width: 200px;
		height: 200px;
		background: blue;
		border-radius: 25px;
		margin: auto;
	}
	.container {
		display: flex;
		align-items: center;
		justify-content: center;
		flex-wrap: wrap;
		height: 100vh;
	}
	.animation {
		width: 100px;
		height: 100px;
		border-radius: 25px;
		animation: infinite alternate 8s ease-in-out morph;
		opacity: 0.5;
		transition: 2s;
	}
	.animation:hover {
	}

	.button {
		position: absolute;
		inset: 0;
		top: 5rem;
		text-align: center;
		
		width: 100px;
		height: 30px;
		box-shadow: 10px 10px 10px 0px #0002,
			0px 0px 0px 0px #F000 inset;
		transition: 0.1s;
	}
	.button:hover {
		box-shadow: 0px 0px 0px 0px #00F0, 10px 10px 10px 0px #0002 inset;
			width: 95px;
			height: 95px;
	}

	@keyframes morph {
		0% {
			box-shadow: 10px 10px 20px -10px #00000025 inset, 0px 0px 0px 0px #00000000 ;
		}
		25% {
			box-shadow: 0px 0px 0px 0px #00000025 inset, 0px 0px 0px 0px #00000020;
		}
		50% {
			box-shadow: 0px 0px 0px 0px #00000025 inset, 10px 10px 10px 0px #00000020;
		}
		75% {
			box-shadow: 10px 10px 20px -10px #00000025 inset, 0px 0px 0px 0px #00000000;
		}
	}
</style>
