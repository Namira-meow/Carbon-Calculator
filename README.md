<!DOCTYPE html>
<html>
  <head> 
  <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Carbon Footprint Calculator</title>
    <link rel="stylesheet" href="style.css">
    </head>
    <body>
        <div class="container">
            <h1>Carbon Footprint Calculator</h1>            
          <form id="carbonForm">
                <label for="electricity">Electricity Usage (kWh):</label>
                <input type="number" id="electricity" name="electricity" required>
                <label for="gas">Natural Gas Usage (therms):</label>
                <input type="number" id="gas" name="gas" required>
                <label for="transportation">Transportation (miles):</label>
                <input type="number" id="transportation" name="transportation" required>
                <button type="submit">Calculate</button>
                </form>
                <div id="result"></div>
            </div>
            <script src="script.js"></script>
        </body>
        </html>
        body {
  font-family: Arial, sans-serif;
   background-color: #f0f8f5; /* light greenish background */
 color: #2c3e50; /* dark bluish text */
   margin: 0;
    padding: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  }
.container {
background-color: #ffffff;
  padding: 30px 40px;
 border-radius: 10px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.1);
  max-width: 400px;
  width: 100%;
  box-sizing: border-box;
}
h1 {
    text-align: center;
  margin-bottom: 25px;
  color: #27ae60; /* green */
  }
label {
 display: block;
  margin-bottom: 8px;
  color: #2c3e50; /* dark bluish text */
  font-weight: 600;
}
input[type="number"] {
  width: 100%;
  padding: 10px;
  margin-bottom: 20px;
  border: 2px solid #27ae60;
  border-radius: 6px;
  box-sizing: border-box;
   transition: border-color 0.3s;
}
  input[type="number"]:focus {
    border-color: #2ecc71; /* lighter green */
      outline: none;
    }
button {
  width: 100%;
  padding: 12px;
  background-color: #27ae60; /* green */
  color: #ffffff;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  transition: background-color 0.3s;
  }
button:hover {
  background-color: #2ecc71; /* lighter green */
  }  
#result {
margin-top: 25px;
font-size: 20px;
 font-weight: 700;
  color: #34495e; /* dark greyish text */
 text-align: center;
}
function calculateFootprint() {
 const electricity = parseFloat(document.getElementById('electricity').value) || 0;
  const gas = parseFloat(document.getElementById('gas').value) || 0;
  const transportation = parseFloat(document.getElementById('transportation').value) || 0;
  const electricityFactor = 0.404; // kg CO2 per kWh
  const gasFactor = 5.31; // kg CO2 per therm
  const transportationFactor = 0.258; // kg CO2 per mile
  const totalFootprint = (electricity * electricityFactor) + (gas * gasFactor) + (transportation * transportationFactor);
 document.getElementById('result').innerText =  `Your estimated carbon footprint is ${totalFootprint.toFixed(2)} kg CO2 per year.`;
  }
document.getElementById('carbonForm').addEventListener('submit', function(event) {
    event.preventDefault(); // prevent page refresh
   calculateFootprint();
  }); 
