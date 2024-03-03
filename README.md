# Raspberry-Pi
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Melatone</title>
<link rel="stylesheet" href="styles.css">
</head>
<body>

<div class="power-switch">
  <input type="checkbox" id="powerToggle">
  <div class="button">
    <svg class="power-off">
      <use xlink:href="#line" class="line" />
      <use xlink:href="#circle" class="circle" />
    </svg>
    <svg class="power-on">
      <use xlink:href="#line" class="line" />
      <use xlink:href="#circle" class="circle" />
    </svg>
  </div>
</div>

<!-- SVG -->
<svg xmlns="http://www.w3.org/2000/svg" style="display: none;">
  <symbol xmlns="http://www.w3.org/2000/svg" viewBox="0 0 150 150" id="line">
    <line x1="75" y1="34" x2="75" y2="58"/>
  </symbol>
  <symbol xmlns="http://www.w3.org/2000/svg" viewBox="0 0 150 150" id="circle">
    <circle cx="75" cy="80" r="35"/>
  </symbol>
</svg>

<script>
const powerToggle = document.getElementById('powerToggle');
const button = document.querySelector('.button');

powerToggle.addEventListener('change', () => {
  if (powerToggle.checked) {
    button.classList.add('active');
  } else {
    button.classList.remove('active');
  }
});
</script>

</body>
</html>

