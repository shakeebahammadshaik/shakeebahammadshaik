- 👋 Hi, I’m @shakeebahammadshaik
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
shakeebahammadshaik/shakeebahammadshaik is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
<!DOCTYPE html>
<html>
<head>
  <title>Customer Information Form</title>
  <style>
    .form-container {
      max-width: 400px;
      margin: 0 auto;
    }
    .form-group {
      margin-bottom: 20px;
    }
    .form-group label {
      display: block;
      margin-bottom: 5px;
    }
  </style>
</head>
<body>
  <div class="form-container">
    <h1>Customer Information Form</h1>
    <form id="customer-form">
      <div class="form-group">
        <label for="customer-name">Customer Name:</label>
        <input type="text" id="customer-name" required>
      </div>
      <div class="form-group">
        <label for="check-in-date">Check-in Date:</label>
        <input type="date" id="check-in-date" required>
      </div>
      <div class="form-group">
        <label for="total-days">Total No of Days:</label>
        <input type="number" id="total-days" required>
      </div>
      <div class="form-group">
        <label for="total-persons">Total No of Persons:</label>
        <input type="number" id="total-persons" required>
      </div>
      <div class="form-group">
        <label for="room-type">Room Type:</label>
        <select id="room-type">
          <option value="deluxe">Deluxe Room</option>
          <option value="suite">Suite Room</option>
        </select>
      </div>
      <div class="form-group">
        <label for="amenities">Amenities:</label>
        <select id="amenities" multiple>
          <option value="ac">AC</option>
          <option value="locker">Locker</option>
        </select>
      </div>
      <div class="form-group">
        <label for="advance-amount">Advance Amount:</label>
        <input type="number" id="advance-amount" required>
      </div>
      <div class="form-group">
        <label for="total-cost">Total Cost:</label>
        <input type="text" id="total-cost" readonly>
      </div>
      <div class="form-group">
        <label for="balance">Balance:</label>
        <input type="text" id="balance" readonly>
      </div>
      <button type="submit">Submit</button>
    </form>
  </div>

  <script>
    document.getElementById('customer-form').addEventListener('submit', function(event) {
      event.preventDefault();

      // Get form values
      var customerName = document.getElementById('customer-name').value;
      var checkInDate = document.getElementById('check-in-date').value;
      var totalDays = parseInt(document.getElementById('total-days').value);
      var totalPersons = parseInt(document.getElementById('total-persons').value);
      var roomType = document.getElementById('room-type').value;
      var amenities = Array.from(document.getElementById('amenities').selectedOptions, option => option.value);
      var advanceAmount = parseInt(document.getElementById('advance-amount').value);

      // Calculate room cost
      var roomRate = (roomType === 'deluxe') ? 2500 : 4000;
      var totalRoomCost = roomRate * totalDays;

      // Calculate amenities cost
      var amenitiesCost = 0;
      if (amenities.includes('ac')) {
        amenitiesCost += 1000;
      }
      if (amenities.includes('locker')) {
        amenitiesCost += 300;
      }
      var totalAmenitiesCost = amenitiesCost * totalDays;

      // Calculate total cost
      var totalCost = totalRoomCost + totalAmenitiesCost;

      // Calculate balance
      var balance = totalCost - advanceAmount;

      // Display calculated values
      document.getElementById('total-cost').value = totalCost;
      document.getElementById('balance').value = balance;
    });
  </script>
</body>
</html>
