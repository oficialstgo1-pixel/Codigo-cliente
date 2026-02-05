#<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Código de Depósito</title>
<style>
 body { font-family: Arial; text-align: center; margin-top: 50px; }
 input, button { padding: 10px; margin: 5px; width: 260px; }
</style>
</head>

<body>

<h2>Consulta tu código de depósito</h2>

<input type="text" id="busqueda" placeholder="Nombre o Cédula">
<br>
<button onclick="buscar()">Consultar</button>

<p id="resultado"></p>

<script>
const clientes = [
 { nombre:"juan perez", cedula:"00112345678", codigo:"JP-1025" },
 { nombre:"maria lopez", cedula:"40298765432", codigo:"ML-2041" },
 { nombre:"carlos gomez", cedula:"03145678901", codigo:"CG-3098" }
 // aquí sigues agregando
];

function buscar(){
 let v = document.getElementById("busqueda").value.toLowerCase().trim();
 let r = document.getElementById("resultado");

 let c = clientes.find(x => x.nombre === v || x.cedula === v);

 r.innerHTML = c
  ? "Tu código fijo de depósito es: <b>"+c.codigo+"</b>"
  : "❌ No encontrado";
}
</script>

<script>
fetch("clientes.json")
  .then(response => response.json())
  .then(clientes => {

    window.buscarCliente = function () {
      const valor = document.getElementById("busqueda").value.trim().toLowerCase();
      const resultado = document.getElementById("resultado");

      const cliente = clientes.find(c =>
        c.cedula === valor || c.nombre.toLowerCase() === valor
      );

      if (cliente) {
        resultado.innerHTML =
          "Nombre: " + cliente.nombre + "<br>" +
          "Código: " + cliente.codigo;
      } else {
        resultado.innerHTML = "Cliente no encontrado";
      }
    };

  });
</script></body><input id="busqueda" placeholder="Cédula o nombre">
<button onclick="buscarCliente()">Buscar</button>

<div id="resultado"></div>
</html> Codigo-cliente
Consulta de codigo de deposito
