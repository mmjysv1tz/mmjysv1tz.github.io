<!DOCTYPE HTML><html>
<head>
<title>Grp12Website</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<link rel="stylesheet"
integrity="sha384-fnmOCqbTlWIlj8LyTjo7mOUStjsKC4pOpQbqyi7RrhN7udi9RwhKkMHpvLbHG9Sr"
crossorigin="anonymous">
<link rel="icon" href="data:,">
<style>
html {font-family: Arial; display: inline-block; text-align: center;}
p { font-size: 1.2rem;}
body { margin: 0;}
.topnav { overflow: hidden; background-color: #005772; color: white; font-size: 1.7rem; }
.content { padding: 20px; }
.card { background-color: white; box-shadow: 2px 2px 12px 1px rgba(140,140,140,.5); }
.cards { max-width: 700px; margin: 0 auto; display: grid; grid-gap: 2rem; grid-template-columns: repeat(auto-fit,
minmax(300px, 1fr)); }
.reading { font-size: 2.8rem; }
.card.temperature { color: #0e7c7b; }
</style>
</head>
<body>
<div class="topnav">
<h3>= GROUP 12 =</h3>
</div>
<div class="content">
<div class="cards">
<div class="card temperature">
<h4><i class="fas fa-thermometer-half"></i> TEMPERATURE</h4><p><span class="reading"><span
id="temp_celcius">%TEMPERATURE_C%</span> &deg;C</span></p>
</div>
<div class="card temperature">
<h4><i class=></i> TEMPERATURE</h4><p><span class="reading"><span
id="temp_fahrenheit">%TEMPERATURE_F%</span> &deg;F</span></p>
</div>
</div>
</div>
<script>
if (!!window.EventSource) {
var source = new EventSource('/events');
source.addEventListener('open', function(e) {
console.log("Events Connected");
}, false);
source.addEventListener('error', function(e) {
if (e.target.readyState != EventSource.OPEN) {
console.log("Events Disconnected");
}
}, false);
source.addEventListener('message', function(e) {
console.log("message", e.data);
}, false);
source.addEventListener('temperature_Celsius', function(e) {
console.log("temperature", e.data);
document.getElementById("temp_celcius").innerHTML = e.data;
}, false);
source.addEventListener('temperature_Fahrenheit', function(e) {
console.log("temperature", e.data);
document.getElementById("temp_fahrenheit").innerHTML = e.data;
}, false);
}
</script>
</body>
</html>
