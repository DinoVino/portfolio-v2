<style lang="css">
    nav{
        text-align: center;
    }
    a{
        text-decoration:none;
    }
</style>

<script>
  let {children} = $props();
</script>

<nav>
    <a href="/">Home </a>
    <a href="/about">About me</a>
    <a href="/projects"> Projects </a>
</nav>
<div class="middle">
    {@render children()}
</div>
