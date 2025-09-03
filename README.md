<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Livestock Management Dashboard</title>
  <link rel="stylesheet" href="Infilink.css">
</head>
<body>
  <header>
    <h1>Livestock Management Dashboard</h1>
  </header>

  <main>
    <section class="add-livestock">
      <h2>Add New Livestock</h2>
      <form id="livestock-form">
        <input type="text" id="animal-id" placeholder="Animal ID" required>
        <input type="text" id="animal-type" placeholder="Animal Type" required>
        <input type="number" id="age" placeholder="Age (years)" required>
        <input type="number" id="weight" placeholder="Weight (kg)" required>
        <button type="submit">Add Livestock</button>
      </form>
    </section>

    <section class="livestock-list">
      <h2>Livestock Records</h2>
      <table id="livestock-table">
        <thead>
          <tr>
            <th>Animal ID</th>
            <th>Type</th>
            <th>Age</th>
            <th>Weight</th>
            <th>Actions</th>
          </tr>
        </thead>
        <tbody>
          <!-- Livestock entries will appear here -->
        </tbody>
      </table>
    </section>
  </main>

  <script src="script.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f4f4f4;
}

header {
  background-color: #4CAF50;
  color: white;
  text-align: center;
  padding: 20px;
}

main {
  padding: 20px;
}

section {
  margin-bottom: 20px;
}

input, button {
  padding: 10px;
  margin: 5px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  background-color: #4CAF50;
  color: white;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

th, td {
  padding: 10px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

th {
  background-color: #f2f2f2;
}
document.getElementById('livestock-form').addEventListener('submit', function(event) {
  event.preventDefault();

  const animalId = document.getElementById('animal-id').value;
  const animalType = document.getElementById('animal-type').value;
  const age = document.getElementById('age').value;
  const weight = document.getElementById('weight').value;

  const table = document.getElementById('livestock-table').getElementsByTagName('tbody')[0];
  const newRow = table.insertRow();

  newRow.innerHTML = `
    <td>${animalId}</td>
    <td>${animalType}</td>
    <td>${age}</td>
    <td>${weight}</td>
    <td><button class="delete-btn">Delete</button></td>
  `;

  newRow.querySelector('.delete-btn').addEventListener('click', function() {
    table.deleteRow(newRow.rowIndex - 1);
  });

  document.getElementById('livestock-form').reset();
});
