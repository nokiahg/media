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
  var map = L.map('map').setView([-22.9711, -43.2247], 16);

  // Adicionando um mapa base (OpenStreetMap)
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
  }).addTo(map);

  // Adicionando camadas dos mapas históricos
  var map1809 = L.imageOverlay(
    'https://raw.githubusercontent.com/nokiahg/media/main/1809.jpeg',
    [[-22.975, -43.229], [-22.968, -43.218]]
  );

  var map1844 = L.imageOverlay(
    'https://raw.githubusercontent.com/nokiahg/media/main/1844.jpeg',
    [[-22.975, -43.229], [-22.968, -43.218]]
  );

  var map2024 = L.imageOverlay(
    'https://raw.githubusercontent.com/nokiahg/media/main/2024.jpeg',
    [[-22.975, -43.229], [-22.968, -43.218]]
  );

  // Controle de linha do tempo para alternar entre camadas
  var timeline = {
    '1809': map1809,
    '1844': map1844,
    '2024': map2024,
  };

  function changeYear(year) {
    Object.values(timeline).forEach(layer => map.removeLayer(layer));
    timeline[year].addTo(map);
  }

  // Interface de controle da linha do tempo
  var timelineControl = L.control({ position: 'topright' });
  timelineControl.onAdd = function () {
    var div = L.DomUtil.create('div', 'timeline-control');
    div.innerHTML = `
      <select id="year" onchange="changeYear(this.value)">
        <option value="1809">1809</option>
        <option value="1844">1844</option>
        <option value="2024">2024</option>
      </select>`;
    return div;
  };
  timelineControl.addTo(map);

  // Inicializando com o mapa de 1809
  changeYear('1809');
</script>
