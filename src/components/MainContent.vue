<template>
    <main class="main-content">
      <section class="hero">
        <h2>Ласкаво просимо до нашого сайту!</h2>
        <p>Тут ви знайдете багато цікавої інформації.</p>
      </section>
  
      <section class="features">
        <div class="feature">
          <h3>Це ми</h3>
          <img class="img_1" src="../assets/images_1.jpeg" alt="images_1.jpeg">
        </div>
        <div class="feature">
          <h3>Трохи юмора</h3>
          <p>Ще один цікавий блок з текстом.</p>
          <img src="../assets/pitoni.jpeg" alt="pitoni.jpeg">
        </div>
        <div class="feature">
          <h3>Особливість 3</h3>
          <img src="../assets/scrooge.jpeg" alt="scrooge.jpeg">
          <p>Програмісти в майбутньому.</p>
        </div>
      </section>
    </main>
  </template>
  
  <style scoped>
  .main-content {
    padding: 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }
  .hero {
    text-align: center;
    margin-bottom: 3rem;
  }
  .features {
    display: flex;
    justify-content: space-around;
  }
  img{
    width: 300px;
    height: auto;
  }
  .feature {
    background-color: #f0f0f0;
    /* padding: 1rem; */
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
    text-align: center;
    flex-basis: 30%;
  }
  .img_1{
    padding: 100px 0 0;
  }
  .feature h3 {
    margin-bottom: 1rem;
    color: #333;
  }
  </style>
  