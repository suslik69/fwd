<script>
	import {base} from "$app/paths";
	import './styles.css';
</script>

<div class="app">
	<header>
		<nav>
			<a href="{base}/">About</a>
			<a href="{base}/xkcd/">XKCD</a>
		</nav>
	</header>

	<main>
		<slot />
	</main>

	<footer>
		<p>visit <a href="https://warthunder.com">warthunder.com</a> to play some tanks...</p>
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
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 64rem;
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

	@media (min-width: 480px) {
		footer {
			padding: 12px 0;
		}
	}

	header {
		display: flex;
		justify-content: space-between;
	}


	nav {
		display: flex;
		justify-content: center;
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 1rem;
		color: white;
		font-weight: 700;
		font-size: 1.6rem;
		text-transform: uppercase;
		letter-spacing: 0.1em;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		background-color: rgb(147, 0, 180);
	}
</style>
