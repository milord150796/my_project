<template>
    <header class="site-header">
      <nav>
        <h1>Тут міг бути ти !!!</h1>
        <ul>
          <li><a href="#">Головна</a></li>
          <li><a href="#">Про нас</a></li>
          <li><a href="#">Контакти</a></li>
        </ul>
      </nav>
    </header>
  </template>
  
  <style scoped>
  .site-header {
    background-color: #333;
    color: white;
    padding: 1rem;
  }
  nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  nav h1 {
    margin: 0;
  }
  nav ul {
    list-style: none;
    display: flex;
    gap: 1rem;
  }
  nav ul li a {
    color: white;
    text-decoration: none;
  }
  nav ul li a:hover {
    text-decoration: underline;
  }
  </style>
  