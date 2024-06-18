<template>
    <div :style="cardStyles" class="card">
      <div class="card-body">
        <h5 class="card-title">{{ title }}</h5>
        <p class="card-text">{{ description }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: {
        type: String,
        required: true
      },
      description: {
        type: String,
        required: true
      },
      width: {
        type: String,
        default: "300px"
      },
      height: {
        type: String,
        default: "200px"
      },
      backgroundColor: {
        type: String,
        default: "#ffffff"
      },
      color: {
        type: String,
        default: "#333333"
      }
    },
    computed: {
      cardStyles() {
        return {
          width: this.width,
          height: this.height,
          backgroundColor: this.backgroundColor,
          color: this.color
        };
      }
    }
  };
  </script>
  
  <style scoped>
  .card {
    border: 1px solid #ccc;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
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
  </style>
  