<!DOCTYPE html>
<html>

<head>
  <title>Melatone</title>
  <link rel="stylesheet" href="styles.css">
  <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.2.0/css/all.css"
    integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ" crossorigin="anonymous">
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
      <line x1="75" y1="34" x2="75" y2="58" />
    </symbol>
    <symbol xmlns="http://www.w3.org/2000/svg" viewBox="0 0 150 150" id="circle">
      <circle cx="75" cy="80" r="35" />
    </symbol>
  </svg>

  <!-- Mobile Hamberger Menu Icon (Mobile Only) -->
  <button onclick="toggleMenu()" id="ham-button" class="ham-button"><i class="fas fa-bars"></i></button>
  <!-- Side Menu Container -->
  <div class="side-menu" id="side-menu">
    <!-- Side Menu Heading-->
    <h3>Menu</h3>
    <!-- Side Menu Links -->
    <a href='#' onclick="toggleSettings(event)"><i class="fas fa-cog"></i> Settings</a>
    <!-- Color Choice Option -->
    <div class="submenu" id="settingsSubMenu" style="display: none;">
      <a href="#" id="colorChoiceLink" class="sub-item"><i class="fas fa-palette"></i> Color Choice</a>
      <a href="#" class="sub-item"><i class="fas fa-volume-up"></i> Sound</a>
      <a href="#" class="sub-item" onclick="toggleLightIntensity()"><i class="fas fa-lightbulb"></i> Light Intensity</a>
    </div>
    <a target='blank' href='https://www.youtube.com/channel/UCVIVmoHr9KPc2fCT3byDp4A'><i class="fab fa-youtube"></i> YouTube</a>
  </div>

  <div class='brand' style="position: absolute; top: 3%; left: 50%; transform: translateX(-50%);">
    <img src="https://i.ibb.co/1G3DNWm/melatone-logo.png" alt="Melatone Logo">
  </div>

  <!-- Placeholder for Color Choice Section -->
  <div id="color-choice-section" style="display: none;">
    <input type="color" id="colorpicker" value="#0000ff">
  </div>

  <!-- Light Intensity Section -->
  <div id="light-intensity-section" style="display: none;">
    <h2>Light Intensity</h2>
    <label>
      Intensity
      <input type="range" id="intensitySlider" min="0" max="100" value="100">
      <span id="intensityDisplay" style="color: white;">100</span>
    </label>
  </div>

  <div id="sound-options-section" style="display: none;">
    <h2>Sound Options</h2>
    <ul>
      <li><button onclick="playAlarm('alarm1.mp3')">Alarm 1</button></li>
      <li><button onclick="playAlarm('alarm2.mp3')">Alarm 2</button></li>
      <li><button onclick="playAlarm('alarm3.mp3')">Alarm 3</button></li>
    </ul>
  </div>

  <!-- JavaScript -->
  <script>
    function toggleMenu() {
      let menu = document.getElementById("side-menu");
      if (menu.style.display === "block") {
        menu.style.display = "none";
      } else {
        menu.style.display = "block";
      }
    }

    function toggleSettings(event) {
      event.preventDefault(); // Prevent default link behavior
      var settingsSubMenu = document.getElementById("settingsSubMenu");
      if (settingsSubMenu.style.display === "none") {
        settingsSubMenu.style.display = "block";
        document.querySelectorAll('.sub-item').forEach(item => {
          item.style.paddingLeft = '20px'; // Add indentation
        });
      } else {
        settingsSubMenu.style.display = "none";
        document.querySelectorAll('.sub-item').forEach(item => {
          item.style.paddingLeft = '0'; // Remove indentation
        });
      }
    }

    function toggleLightIntensity() {
      var lightIntensitySection = document.getElementById("light-intensity-section");
      if (lightIntensitySection.style.display === "none") {
        lightIntensitySection.style.display = "block";
      } else {
        lightIntensitySection.style.display = "none";
      }
    }

    function playAlarm(sound) {
      var audio = new Audio(sound);
      audio.play();
    }

    document.getElementById("colorChoiceLink").addEventListener("click", function(event) {
      event.preventDefault(); // Prevent default link behavior
      event.stopPropagation(); // Prevent event from propagating to parent
      var colorChoiceSection = document.getElementById("color-choice-section");
      if (colorChoiceSection.style.display === "none") {
        colorChoiceSection.style.display = "block";
      } else {
        colorChoiceSection.style.display = "none";
      }
    });

    // Slider action for light intensity
    var intensitySlider = document.getElementById("intensitySlider");
    var intensityDisplay = document.getElementById("intensityDisplay");

    intensitySlider.addEventListener("input", function() {
      var newIntensity = intensitySlider.value;
      intensityDisplay.innerText = newIntensity;
      // Your further actions based on light intensity value can be added here
    });
  </script>
</body>

</html>
