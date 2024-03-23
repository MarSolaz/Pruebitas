<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora de Valor en Horas</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #d1c4e9;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
        }
        .container {
            background-color: #f3e5f5;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
            max-width: 400px;
            width: 100%;
        }
        h1 {
            text-align: center;
            color: #512da8;
            font-size: 28px;
            margin-bottom: 20px;
            text-transform: uppercase;
            letter-spacing: 2px;
        }
        form {
            display: flex;
            flex-direction: column;
        }
        label {
            margin-bottom: 5px;
            color: #512da8;
            font-size: 14px;
        }
        input[type="text"], input[type="number"] {
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid #ba68c8;
            border-radius: 5px;
            font-size: 16px;
            background-color: #fff;
        }
        button {
            padding: 10px;
            background-color: #7e57c2;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 16px;
            transition: background-color 0.3s;
        }
        button:hover {
            background-color: #673ab7;
        }
        .resultado {
            margin-top: 20px;
            text-align: center;
            font-weight: bold;
            color: #7e57c2;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Calculadora de Valor en Horas</h1>
        <form id="calculadoraForm">
            <label for="salario">Salario mensual (en $):</label>
            <input type="number" id="salario" name="salario" min="0" step="any" required>

            <label for="horas_trabajo">Horas de trabajo al mes:</label>
            <input type="number" id="horas_trabajo" name="horas_trabajo" min="1" step="any" required>

            <label for="producto">Producto o servicio a comprar:</label>
            <input type="text" id="producto" name="producto" required>

            <label for="precio">Precio del producto o servicio (en $):</label>
            <input type="number" id="precio" name="precio" min="0" step="any" required>

            <button type="button" onclick="calcularValorHoras()">Calcular</button>
        </form>

        <div id="resultado" class="resultado"></div>
    </div>

    <script>
        function calcularValorHoras() {
            var salario = parseFloat(document.getElementById('salario').value);
            var horasTrabajo = parseFloat(document.getElementById('horas_trabajo').value);
            var producto = document.getElementById('producto').value;
            var precio = parseFloat(document.getElementById('precio').value);

            if (!isNaN(salario) && !isNaN(horasTrabajo) && !isNaN(precio)) {
                var salarioPorHora = salario / horasTrabajo;
                var horasParaObjeto = precio / salarioPorHora;
                var resultadoDiv = document.getElementById('resultado');
                resultadoDiv.innerHTML = "Para comprar " + producto + " necesitas trabajar " + horasParaObjeto.toFixed(2) + " horas.";
            } else {
                alert("Por favor, ingrese valores válidos para el salario mensual, las horas de trabajo y el precio del producto o servicio.");
            }
        }
    </script>
</body>
</html>
