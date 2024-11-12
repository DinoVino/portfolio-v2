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

<nav class="suse">
    <a href="/">Home </a>
    <a href="/about">About me</a>
    <div class="dropdown">
        <a href="/projects"> Projects </a>
        <div class="content">
            <a href="/projects/nixos">test</a>
            <a href="/projects/innerev">twst</a>
        </div>

    </div>
    
    
</nav>
<div class="middle">
    {@render children()}
</div>
