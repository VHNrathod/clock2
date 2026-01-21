<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Colorful Digital Clock</title>
  <style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #ff9a9e, #fad0c4, #fad0c4, #fbc2eb, #a18cd1);
      background-size: 400% 400%;
      animation: gradientShift 10s ease infinite;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    @keyframes gradientShift {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }

    .clock {
      font-size: 5em;
      color: white;
      background: rgba(0, 0, 0, 0.3);
      padding: 20px 40px;
      border-radius: 20px;
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
    }
  </style>
</head>
<body>

  <div class="clock" id="clock">00:00:00 AM</div>

  <script>
    function updateClock() {
      const now = new Date();
      let hours = now.getHours();
      const minutes = now.getMinutes();
      const seconds = now.getSeconds();
      const ampm = hours >= 12 ? 'PM' : 'AM';

      hours = hours % 12;
      hours = hours ? hours : 12; // the hour '0' should be '12'

      const formattedTime = [
        hours.toString().padStart(2, '0'),
        minutes.toString().padStart(2, '0'),
        seconds.toString().padStart(2, '0')
      ].join(':') + ' ' + ampm;

      document.getElementById('clock').textContent = formattedTime;
    }

    // Update every second
    setInterval(updateClock, 1000);
    updateClock(); // initial call
  </script>

</body>
</html>
