<style>
  body {
    margin: 0;
    padding: 0;
    font-family: Arial, sans-serif;
  }
  .navbar {
    background-color: #007bff;
    padding: 0;
    color: white;
    padding: 10px 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    width: 98%; /* Ensure navbar spans full width */
  }
  .navbar .brand {
    font-size: 1.5rem;
    font-weight: bold;
  }
  .navbar .nav-links {
    display: flex;
    gap: 15px;
  }
  .navbar .nav-link {
    text-decoration: none;
    color: white;
    padding: 8px 16px;
    border-radius: 4px;
    transition: background-color 0.3s;
  }
  .navbar .nav-link:hover {
    background-color: #0056b3;
  }
  .navbar .menu-toggle {
    display: none;
  }
  .navbar .menu {
    display: flex;
  }
  @media (max-width: 768px) {
    .navbar .menu {
      display: none;
      flex-direction: column;
      width: 100%;
      position: absolute;
      top: 60px;
      left: 0;
      background-color: #007bff;
    }
    .navbar .menu.open {
      display: flex;
    }
    .navbar .menu-toggle {
      display: block;
      cursor: pointer;
      font-size: 1.5rem;
    }
  }
  /* Checkbox hack for menu toggle */
  .navbar input[type="checkbox"] {
    display: none;
  }
  .navbar input[type="checkbox"]:checked ~ .menu {
    display: flex;
  }
</style>

<nav class="navbar">
  <span class="brand">Brand</span>
  <input type="checkbox" id="menu-toggle" class="menu-toggle" />
  <label for="menu-toggle" class="menu-toggle">&#9776;</label>
  <div class="menu">
    <a href="/" class="nav-link">Home</a>
    <a href="/about_us" class="nav-link">About</a>
    <a href="/pages" class="nav-link">Pages</a>
    <a href="/contact" class="nav-link">Contact</a>
  </div>
</nav>
