<script>
  import "../app.css";
</script>

<nav
  class="navbar  bg-white/80
backdrop-blur-md shadow-md w-full
sticky top-0 left-0 right-0 z-10"
>
  <div class="mycompany">
    <img src="/logo.png" alt="" class="log0" />
  </div>

  <div class="navigate-menu mx-4">
    <ul class="nav-menu">
      <li class="nav-list">
        <a href="/index" class="nav-link">Home</a>
      </li>
      <li class="nav-list">
        <a href="/create" class="nav-link">Create patient</a>
      </li>
      <li class="nav-list">
        <a href="/view" class="nav-link">View patient</a>
      </li>
    </ul>
  </div>
</nav>

<slot />

<style>
  .navbar {
    /* border: 1px solid red; */
    height: 4.56rem;
    display: flex;
    align-items: center;
    padding-top: 10px;
  }
  .mycompany {
    /* border: 1px solid green; */
    margin-left: 1.5rem;
    max-width: 7rem;
    display: block;

  }
  .nav-menu {
    display: flex;
  }
  .nav-list {
    margin-left: 2rem;
  }
  .nav-link {
    font-size: 20px;
    /* font-weight: bold; */
  }
</style>
