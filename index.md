# Mapa Interativo do Jardim Botânico - 1844  

Explore a evolução do Jardim Botânico e ajuste a transparência do mapa histórico usando o controle deslizante abaixo.

<div id="map" style="height: 600px; margin-bottom: 10px;"></div>

<label for="opacityRange">Transparência: </label>
<input type="range" id="opacityRange" min="0" max="1" step="0.1" value="1">

<!-- Adicionando as bibliotecas Leaflet.js -->
<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css"
/>
<script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>

<script>
  // Inicializando o mapa
  var map = L.map('map').setView([-22.9711, -43.2247], 13); // Coordenadas centrais

  // Adicionando o mapa base (OpenStreetMap)
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
  }).addTo(map);

  // Adicionando o mapa histórico de 1844 como camada
  var map1844 = L.imageOverlay(
    'https://raw.githubusercontent.com/nokiahg/media/main/1844_georeferenced.jpeg',
    [[-22.9314, -43.2706], [-23.0170, -43.1776]], // Coordenadas ajustadas
    { opacity: 1 } // Inicia com opacidade 100%
  );

  // Exibir a camada de 1844 no início
  map1844.addTo(map);

  // Controle de Transparência (Slider)
  var opacityRange = document.getElementById('opacityRange');
  opacityRange.addEventListener('input', function () {
    var opacity = parseFloat(this.value); // Converte para número
    map1844.setOpacity(opacity); // Altera a opacidade da camada
  });
</script>
