<!DOCTYPE html>
<head>
	<link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css"
   crossorigin=""/>
   	<script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"
     crossorigin=""></script>	
   <style>
		#map { height: 900px; }
</style>
</head>
<body>
	<div id='map'></div>
	<script>
	
		var desIcon = L.icon({
			iconUrl: 'https://i.imgur.com/7f3YO2g.png?1',
			iconsize: [50, 50],
			iconAnchor: [25, 25]});
		
		var joiIcon = L.icon({
			iconUrl: 'https://i.imgur.com/k3sMRPm.png?2',
			iconsize: [50, 50],
			iconAnchor: [25, 25]});

		var rouIcon = L.icon({
			iconUrl: 'https://i.imgur.com/C6bDqHM.png?1',
			iconsize: [50, 50],
			iconAnchor: [25, 25]});
			
		var eleIcon = L.icon({
			iconUrl: 'https://i.imgur.com/V4tqYdA.png?1',
			iconsize: [50, 50],
			iconAnchor: [25, 25]});

		var celIcon = L.icon({
			iconUrl: 'https://i.imgur.com/ssczcMk.png?1',
			iconsize: [50, 50],
			iconAnchor: [25, 25]});


	
		var desmanches = L.layerGroup();
		var joias = L.layerGroup();
		var roupas = L.layerGroup();
		var eletronicos = L.layerGroup();
		var celular = L.layerGroup();
		var gangues = L.layerGroup();
		
		L.marker([15174,18751], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche da pedreira'),
		L.marker([7228,15130], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche atras do galpão'),
		L.marker([6856,14545], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche atras da mecanica'),
		L.marker([6246,15161], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche embaixo da ponte'),
		L.marker([5658,14775], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche dentro do galpão'),
		L.marker([5319,16584], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche da garagem'),
		L.marker([4228,16056], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche dentro dos galpões'),
		L.marker([3290,15475], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche dentro do galpão inferior'),
		L.marker([6123,13746], {icon: desIcon}).addTo(desmanches).bindPopup('desmanches da oficina destruida'),
		L.marker([5481,13399], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche atras do cabelereiro');
		L.marker([5973,12194], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche atras da bennys');
		L.marker([5253,11737], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche dentro do galpão');
		L.marker([4337,10098], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche atras da los santos custom');
		L.marker([4171,11756], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche do lado da lona');
		L.marker([4300,13194], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche perto dos vagos');
		L.marker([5265,13051], {icon: desIcon}).addTo(desmanches).bindPopup('desmanche no beco');

		
		L.marker([5547,10054], {icon: joiIcon}).addTo(joias).bindPopup('joias da praia');
		L.marker([7909,9198], {icon: joiIcon}).addTo(joias).bindPopup('joias na esquina');
		L.marker([6864,13439], {icon: joiIcon}).addTo(joias).bindPopup('joias na loja');
		L.marker([6064,13130], {icon: joiIcon}).addTo(joias).bindPopup('joias perto do Vanilla');
		
		L.marker([5378,10163], {icon: rouIcon}).addTo(roupas).bindPopup('roupas na praia');
		L.marker([6486,11350], {icon: rouIcon}).addTo(roupas).bindPopup('roupas no estacionamento');

		
		L.marker([7136,13575], {icon: eleIcon}).addTo(eletronicos).bindPopup('Eletronicos na esquina da loja de maconha');
		L.marker([6715,12591], {icon: eleIcon}).addTo(eletronicos).bindPopup('Eletronicos na loja');

		L.marker([7587,9855], {icon: celIcon}).addTo(celular).bindPopup('Celurares no beco');
		L.marker([7076,13781], {icon: celIcon}).addTo(celular).bindPopup('Celurares embaixo da ponte');
		L.marker([19753,16401], {icon: celIcon}).addTo(celular).bindPopup('Celurares em grapeseed');

		
		var ballas = L.polygon([ 
		[4819.906651, 12539.305742], [4999.737346, 12714.696173],[4728.881238, 13132.080996],[4551.270675, 12863.445019]],
		{color: 'purple', fillColor: '#9932CC', fillOpacity: 0.5, radius: 500}
		).addTo(gangues).bindPopup("ballas");
		

		var map = L.map('map', { crs: L.CRS.Simple, minZoom: -4 , maxZoom: -0.5 , zoomDelta: 0.25,  zoomSnap: 0});
		var bounds = [[0,0], [27690,27690]];
		
		var roadmap = L.imageOverlay('http://blog.damonpollard.com/wp-content/uploads/2013/09/GTAV_ROADMAP_8192x8192.png', bounds )   ;
		var satellite = L.imageOverlay('http://blog.damonpollard.com/wp-content/uploads/2013/09/GTAV_SATELLITE_8192x8192.png', bounds );
		var atlus = L.imageOverlay('GTAV_ATLUS_8192x8192.png', bounds );

		var BaseMaps = {
			"Roadmap": roadmap,
			"Satellite": satellite,
			"Atlus": atlus
		};
			
		
		map.fitBounds(bounds);
		
		var overlays = {
			"Desmanches": desmanches,
			"Joias": joias,
			"Roupas": roupas,
			"Eletronicos": eletronicos,
			"Celulares": celular,
			"Gangues": gangues,
		};
		
		L.control.layers(BaseMaps, overlays).addTo(map);
		
		var popup = L.popup();
		
		function onMapClick(e) {
		popup
			.setLatLng(e.latlng)
			.setContent(e.latlng.toString())
			.openOn(map);
	};
	
	L.tileLayer(
  'https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: 'Creator © <a href="https://twitter.com/snowmegda">Megda</a>',
    maxZoom: 18
  }).addTo(map);
	
	map.on('click', onMapClick);
	
	
	
	</script>

</body>
</html>

