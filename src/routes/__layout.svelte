<script>
	import Navbar from '../components/Navbar.svelte';

	import '../app.css';
	import Footer from '../components/Footer.svelte';
</script>

<svelte:head>
	<link
		rel="stylesheet"
		href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.7.0/css/all.min.css"
		integrity="sha512-gRH0EcIcYBFkQTnbpO8k0WlsD20x5VzjhOA1Og8+ZUAhcMUCvd+APD35FJw3GzHAP3e+mP28YcDJxVr745loHw=="
		crossorigin="anonymous"
		referrerpolicy="no-referrer"
	/>
</svelte:head>

<div>
	<Navbar />
	<div class="container mx-auto">
		<slot />
	</div>
	<Footer />
</div>
