<script>
  let { children } = $props();
</script>

<nav class="navbar navbar-expand-sm navbar-dark" style="background-color: rgba(0, 0, 0, 0.7);">
  <div class="container-fluid">
    <a class="navbar-brand" href="/#">Site do DW4 :)</a>
    <button
      class="navbar-toggler"
      type="button"
      data-bs-toggle="collapse"
      data-bs-target="#navbarSupportedContent"
      aria-controls="navbarSupportedContent"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarSupportedContent">
      <ul class="navbar-nav">

        <li class="nav-item">
          <a class="nav-link" href="/Dieta">Guia p/ Dieta</a>
        </li>

        <li class="nav-item">
          <a class="nav-link" href="/Micronutrientes">Micronutrientes e Alimentos Ricos</a>
        </li>

        <li class="nav-item">
          <a class="nav-link" href="/METABOLISMO">Calcule seu Gasto Calorico</a>
        </li>

      </ul>
    </div>
  </div>
</nav>

{@render children()}

<style>
  .navbar-nav .nav-link:hover {
    color: hsl(54, 42%, 95%);
  }
</style>
