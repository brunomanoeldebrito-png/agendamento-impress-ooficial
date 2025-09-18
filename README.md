body {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background: #f9f9f9 url('https://i.imgur.com/4ZQzJ0s.png') no-repeat center center fixed;
  background-size: cover;
  margin: 0;
  padding: 0;
  position: relative;
  min-height: 100vh;
}

body::before {
  content: "";
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(255, 255, 255, 0.85);
  z-index: 0;
}

.container {
  max-width: 720px;
  margin: 40px auto;
  background: #fff;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  position: relative;
  z-index: 1;
}

h1 {
  text-align: center;
  background-color: #000;
  color: #fff;
  padding: 20px;
  border-radius: 8px;
  font-size: 2rem;
  margin-bottom: 20px;
}

h2, h3 {
  text-align: center;
  color: #333;
  margin-top: 30px;
  margin-bottom: 10px;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin: 20px 0;
  font-size: 16px;
}

th, td {
  border: 1px solid #ccc;
  padding: 12px;
  text-align: center;
}

th {
  background-color: #28a745;
  color: #fff;
}

tbody tr:nth-child(even) {
  background-color: #f9f9f9;
}

tbody tr:hover {
  background-color: #eafaf1;
}

button {
  background-color: #28a745;
  color: white;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin-top: 20px;
  padding: 10px 15px;
  border: none;
  border-radius: 6px;
  width: 100%;
  font-size: 16px;
}

button:hover {
  background-color: #218838;
}

input, select {
  width: 100%;
  padding: 10px;
  margin-top: 5px;
  margin-bottom: 15px;
  border-radius: 6px;
  border: 1px solid #ccc;
  font-size: 16px;
  box-sizing: border-box;
}

.hidden {
  display: none;
}

@media (max-width: 600px) {
  .container {
    padding: 20px;
    margin: 10px;
  }

  h1 {
    font-size: 1.5rem;
    padding: 15px;
  }

  table th, table td {
    padding: 10px;
    font-size: 14px;
  }
}


