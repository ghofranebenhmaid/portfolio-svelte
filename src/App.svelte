<script>
	import { Router, Route } from "svelte-navigator";
	import Home from "./pages/home.svelte";
	import Projects from "./pages/projects.svelte";

	
</script>

<Router>
	<!-- <Route path="/" component={Home} /> -->
	<Route path="/" component={Home} />
	<Route path="projects" component={Projects} />

</Router>

<style lang="scss" global>
  @import "./styles/style.scss";
  @import "./styles/globals.scss";
</style>