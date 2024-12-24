<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Copiar Código</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 20px;
    }
    .container {
      max-width: 600px;
      margin: 0 auto;
      text-align: center;
    }
    .code-box {
      background-color: #f4f4f4;
      border: 1px solid #ccc;
      border-radius: 5px;
      padding: 15px;
      text-align: left;
      font-family: monospace;
      white-space: pre-wrap;
      overflow-x: auto;
    }
    button {
      margin-top: 10px;
      padding: 10px 20px;
      background-color: #4CAF50;
      color: white;
      border: none;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background-color: #45a049;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>archivo.js</h1>
    <button onclick="copiarCodigo()">Copiar Código</button>
    <div id="codigo" class="code-box">
      $nomention<br>
      hola
    </div>
  </div>

  <script>
    function copiarCodigo() {
      const codigo = document.getElementById('codigo').innerText;
      navigator.clipboard.writeText(codigo)
        .then(() => alert('¡Código copiado al portapapeles!'))
        .catch(err => alert('Error al copiar el código: ' + err));
    }
  </script>
</body>
</html>

