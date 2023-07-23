# Data-visualization-javascript-script.js
document.addEventListener("DOMContentLoaded", function () {
    const dataForm = document.getElementById("dataForm");
    const dataInput = document.getElementById("dataInput");
    const barChart = document.getElementById("barChart").getContext("2d");
    let chart = null;
  
    dataForm.addEventListener("submit", function (event) {
      event.preventDefault();
  
      const data = dataInput.value.split(",").map(Number);
      if (!data || !Array.isArray(data) || data.some(isNaN)) {
        alert("Invalid input. Please enter comma-separated numbers.");
        return;
      }
  
      if (chart) {
        chart.destroy();
      }
  
      chart = new Chart(barChart, {
        type: "bar",
        data: {
          labels: data.map((value, index) => `Data ${index + 1}`),
          datasets: [
            {
              label: "Data Visualization",
              data: data,
              backgroundColor: "rgba(75, 192, 192, 0.6)",
              borderWidth: 1,
            },
          ],
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          scales: {
            yAxes: [
              {
                ticks: {
                  beginAtZero: true,
                  },
              },
            ],
          },
        },
      });
    });
  });
