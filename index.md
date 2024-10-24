# Evolução do Jardim Botânico do Rio de Janeiro  
## Mapa Interativo: 1809 - 1844 - 2024  

Explore a evolução do Jardim Botânico ao longo do tempo utilizando o mapa interativo abaixo.

<div id="map" style="height: 600px;"></div>

<!-- Adicionando as bibliotecas Leaflet.js -->
<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css"
/>
<script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>

<script>
  // Inicializando o mapa com Leaflet.js
  var map = L.map('map').setView([-22.9711, -43.2247], 13); // Coordenadas centrais do Jardim Botânico

  // Adicionando um mapa base (OpenStreetMap)
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
  }).addTo(map);

  // Adicionando o mapa de 1844 como camada
  var map1844 = L.imageOverlay(
    'https://raw.githubusercontent.com/nokiahg/media/main/1844.jpeg',
    [[-22.9314, -43.2706], [-23.0170, -43.1776]] // Coordenadas do mapa
  );

  // Exibindo o mapa de 1844 na inicialização
  map1844.addTo(map);
</script>


  // Inicializando com o mapa de 1809
  changeYear('1809');
</script>
