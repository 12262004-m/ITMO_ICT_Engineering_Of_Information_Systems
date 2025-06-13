<template>
  <div class="dashboard-container">
    <h1 class="title">График распределения показателей: Россия</h1>

    <div class="metrics">
      <div class="card">
        <h2>Рост</h2>
        <p>+4.2%</p>
      </div>
      <div class="card">
        <h2>Среднее</h2>
        <p>158 млрд</p>
      </div>
      <div class="card">
        <h2>Прогноз</h2>
        <p>170 млрд к 2026</p>
      </div>
    </div>

    <div class="chart-container">
      <canvas ref="canvasRef"></canvas>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Chart from 'chart.js/auto'

const canvasRef = ref(null)

const chartData = {
  labels: [2018, 2019, 2020, 2021, 2022, 2023],
  datasets: [
    {
      label: 'ВВП (млрд $)',
      data: [140, 145, 138, 150, 155, 160],
      borderColor: '#3771f3',
      backgroundColor: 'rgba(55, 113, 243, 0.2)',
      fill: true,
      tension: 0.3
    }
  ]
}

onMounted(() => {
  new Chart(canvasRef.value, {
    type: 'line',
    data: chartData,
    options: {
      responsive: true,
      plugins: {
        legend: {
          position: 'top'
        },
        title: {
          display: true,
          text: 'ВВП по годам'
        }
      }
    }
  })
})
</script>

<style scoped>
.dashboard-container {
  padding: 2rem;
  color: #1F2937;
}

.title {
  font-size: 2rem;
  margin-bottom: 2rem;
  text-align: center;
  color: white;
}

.metrics {
  display: flex;
  gap: 1rem;
  justify-content: center;
  margin-bottom: 2rem;
}

.card {
  background-color: #f3f4f6;
  padding: 1rem 2rem;
  border-radius: 10px;
  text-align: center;
  min-width: 150px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.05);
}

.card h2 {
  font-size: 1rem;
  color: #6b7280;
  margin-bottom: 0.5rem;
}

.card p {
  font-size: 1.5rem;
  font-weight: bold;
}

.chart-container {
  max-width: 700px;
  margin: 0 auto;
}
</style>
