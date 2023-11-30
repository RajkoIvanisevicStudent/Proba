<script>
	import Header from './Header.svelte';
	import './styles.css';
</script>

<div class="app">
	<Header />

	<main>
		<div id="Navigation">
			<ul>
				<li>
					<a href="/bilansStanja"> Bilans stanja </a>
				</li>
				<li>
					<a href="/bilansStanja"> Bilans uspeha </a>
				</li>
			</ul>
		</div>
		<slot />
	</main>

	<footer>
		<!-- <p>visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to learn SvelteKit</p> -->
		<p>@TF, Novi Sad, 2023.</p>
	</footer>
</div>

<style>
	.app {
		display: flex;
		flex-direction: column;
		min-height: 100vh;
	}

	main {
		flex: 1;
		display: flex;
		/* flex-direction: column; */
		padding: 1rem;
		width: 100%;
		/* max-width: 64rem; */
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding: 12px;
	}

	footer a {
		font-weight: bold;
	}

	#Navigation {
		background-color: gray;
		border-radius: 10px;
	}

	#Navigation > ul {
		list-style-type: none;
		padding: 10px;
		margin: 0;
	}

	#Navigation > ul > li {
		text-decoration: none;
		margin: 15px;
		border-radius: 10px;
		background-color: lightgray;
		display: flex;
		justify-content: center;
	}

	#Navigation > ul > li:hover {
		box-shadow: 2px 2px 3px black;
		scale: 1.05;
	}

	#Navigation a {
		color: black;	
		padding: 10px;
	}

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}
</style>
