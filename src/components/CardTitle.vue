<template>
    <div class="card">
      <img :src="image" class="card-img-top" :alt="alt">
      <div class="card-body">
        <h5 class="card-title">{{ title }}</h5>
        <p class="card-text">{{ description }}</p>
        <a href="#" class="btn btn-primary">Ver más</a>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      image: String,
      alt: String,
      title: String,
      description: String
    }
  };
  </script>
  
  <style scoped>
  .card {
    width: 18rem;
    margin: 20px;
    border: 1px solid #ccc;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  
  .card-img-top {
    width: 100%;
    height: 180px;
    object-fit: cover;
  }
  
  .card-body {
    padding: 20px;
  }
  
  .card-title {
    font-size: 1.25rem;
    font-weight: bold;
  }
  
  .card-text {
    margin-top: 10px;
    color: #666;
  }
  
  .btn {
    margin-top: 10px;
  }
  </style>
  