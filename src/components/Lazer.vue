<template>
    <div class="container">
      <div class="running-text">
        <p>Чому програмісти люблять темряву? Бо в темряві не видно багів!</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'RunningText',
  };
  </script>
  
  <style scoped>
  .container {
    width: 100%;
    height: 20vh;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: #000;
    color: #fff;
    overflow: hidden;
  }
  
  .running-text {
    position: relative;
    white-space: nowrap;
    font-size: 2rem;
    font-family: Arial, sans-serif;
    animation: scroll-text 10s linear infinite;
  }
  
  @keyframes scroll-text {
    0% {
      transform: translateX(100%);
    }
    100% {
      transform: translateX(-100%);
    }
  }
  </style>
  