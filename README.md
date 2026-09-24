<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Beaga Semi-Jóias - Calculadora</title>
  <style>
    * {
      box-sizing: border-box;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }
    body {
      background-color: #f4f6f8;
      margin: 0;
      padding: 20px;
      display: flex;
      justify-content: center;
    }
    .container {
      background-color: #ffffff;
      width: 100%;
      max-width: 450px;
      border-radius: 16px;
      padding: 24px;
      box-shadow: 0 4px 20px rgba(0,0,0,0.08);
    }
    h1 {
      color: #1a1a1a;
      font-size: 22px;
      text-align: center;
      margin-top: 0;
      margin-bottom: 6px;
    }
    p.subtitle {
      color: #666;
      font-size: 14px;
      text-align: center;
      margin-bottom: 24px;
    }
    .form-group {
      margin-bottom: 18px;
    }
    label {
      display: block;
      font-size: 14px;
      font-weight: 600;
      color: #333;
      margin-bottom: 6px;
    }
    input {
      width: 100%;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 16px;
      outline: none;
      transition: border-color 0.2s;
    }
    input:focus {
      border-color: #d4af37;
    }
    button {
      width: 100%;
      background-color: #d4af37;
      color: #fff;
      border: none;
      border-radius: 8px;
      padding: 14px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      margin-top: 10px;
      transition: background-color 0.2s;
    }
    button:hover {
      background-color: #b89628;
    }
    .result-box {
      margin-top: 24px;
      background-color: #faf8f2;
      border: 1px solid #e8dfc4;
      border-radius: 10px;
      padding: 16px;
      display: none;
    }
    .result-row {
      display: flex;
      justify-content: space-between;
      margin-bottom: 8px;
      font-size: 15px;
      color: #444;
    }
    .result-row.total {
      font-size: 18px;
      font-weight: bold;
      color: #1a1a1a;
      border-top: 1px solid #d4af37;
      padding-top: 10px;
      margin-top: 10px;
      margin-bottom: 0;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Beaga Semi-Jóias</h1>
    <p class="subtitle">Calculadora de Custo e Venda</p>

    <div class="form-group">
      <label for="peso">Peso da Peça (g):</label>
      <input type="number" id="peso" step="0.01" placeholder="Ex: 5.5">
    </div>

    <div class="form-group">
      <label for="cotacao">Cotação do Ouro (R$/g):</label>
      <input type="number" id="cotacao" step="0.01" placeholder="Ex: 300.00">
    </div>

    <div class="form-group">
      <label for="maodeobra">Mão de Obra / Custo Fixo (R$):</label>
      <input type="number" id="maodeobra" step="0.01" placeholder="Ex: 15.00">
    </div>

    <div class="form-group">
      <label for="lucro">Margem de Lucro (%):</label>
      <input type="number" id="lucro" step="1" placeholder="Ex: 100">
    </div>

    <button onclick="calcular()">Calcular Custo</button>

    <div id="resultado" class="result-box">
      <div class="result-row">
        <span>Custo do Metal:</span>
        <span id="resMetal">R$ 0,00</span>
      </div>
      <div class="result-row">
        <span>Mão de Obra:</span>
        <span id="resMaoDeObra">R$ 0,00</span>
      </div>
      <div class="result-row">
        <span>Custo Total:</span>
        <span id="resCustoTotal">R$ 0,00</span>
      </div>
      <div class="result-row total">
        <span>Preço de Venda:</span>
        <span id="resPrecoVenda">R$ 0,00</span>
      </div>
    </div>
  </div>

  <script>
    function calcular() {
      const peso = parseFloat(document.getElementById('peso').value) || 0;
      const cotacao = parseFloat(document.getElementById('cotacao').value) || 0;
      const maodeobra = parseFloat(document.getElementById('maodeobra').value) || 0;
      const lucro = parseFloat(document.getElementById('lucro').value) || 0;

      const custoMetal = peso * cotacao;
      const custoTotal = custoMetal + maodeobra;
      const precoVenda = custoTotal * (1 + (lucro / 100));

      document.getElementById('resMetal').innerText = 'R$ ' + custoMetal.toFixed(2).replace('.', ',');
      document.getElementById('resMaoDeObra').innerText = 'R$ ' + maodeobra.toFixed(2).replace('.', ',');
      document.getElementById('resCustoTotal').innerText = 'R$ ' + custoTotal.toFixed(2).replace('.', ',');
      document.getElementById('resPrecoVenda').innerText = 'R$ ' + precoVenda.toFixed(2).replace('.', ',');

      document.getElementById('resultado').style.display = 'block';
    }
  </script>

</body>
</html>
