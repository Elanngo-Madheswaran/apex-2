<script>
	import { Navbar } from '$components';
	import '../app.css';
	let { children } = $props();
</script>


<Navbar />
{@render children()}
