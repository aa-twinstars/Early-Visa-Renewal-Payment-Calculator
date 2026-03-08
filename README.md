# Early-Visa-Renewal-Payment-Calculator
This is to identify what is the exact cost based on the last visa processed for the employee.
<!DOCTYPE html>
<html>
<head>
<title>Early Visa Renewal Payment Calculator</title>

<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap" rel="stylesheet">

<style>
body {
    font-family: 'Poppins', sans-serif;
    background: #ffffff;
    margin: 0;
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

.container {
    width: 400px;
    background: #ffffff;
    padding: 30px;
    border-radius: 12px;
    box-shadow: 0 8px 20px rgba(0,0,0,0.1);
    text-align: center;
}

h2 {
    background: linear-gradient(90deg, #4B00FF, #FF1493, #FF4500);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    font-weight: 600;
    font-size: 22px;
    margin-bottom: 25px;
}

input, select, button {
    width: 100%;
    padding: 12px;
    margin-top: 10px;
    margin-bottom: 15px;
    border: 1px solid #ddd;
    border-radius: 8px;
    font-family: 'Poppins', sans-serif;
    font-size: 14px;
}

button {
    background: linear-gradient(90deg, #4B00FF, #FF1493, #FF4500);
    color: #ffffff;
    font-weight: 600;
    border: none;
    cursor: pointer;
    transition: 0.3s;
}

button:hover {
    opacity: 0.85;
}

.tooltip {
    font-size: 12px;
    color: #555555;
    margin-top: -10px;
    margin-bottom: 10px;
}

.result {
    font-weight: 500;
    font-size: 16px;
    margin-top: 15px;
}
</style>

</head>

<body>

<div class="container">

<h2>Early Visa Renewal Payment Calculator</h2>

<label>Employee Name</label>
<input type="text" id="employeeName" placeholder="Enter Employee Name">

<label>Current Visa Expiry Date</label>
<input type="date" id="expiry">

<label>Last Visa Process</label>
<select id="process">
<option value="">Select</option>
<option value="2">New Visa</option>
<option value="3">New Visa + Change of Status</option>
<option value="1">Visa Renewal</option>
</select>

<div class="tooltip">
This is to identify what is the exact cost based on the last visa processed for the employee.
</div>

<button onclick="calculate()">Calculate</button>

<div class="result">
Remaining Days in Current Visa: <span id="days">0</span><br><br>
Employee Payable Amount (AED): <span id="amount">0</span>
</div>

</div>

<script>
function calculate(){
    let expiry = new Date(document.getElementById("expiry").value);
    let today = new Date();

    let diffTime = expiry - today;
    let days = Math.ceil(diffTime / (1000 * 60 * 60 * 24));
    if(days < 0){ days = 0; }

    let cost = document.getElementById("process").value;
    let total = days * cost;

    document.getElementById("days").innerText = days;
    document.getElementById("amount").innerText = total;
}
</script>

</body>
</html>
