<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cálculo de Risco Familiar</title>
    <style>
        table {
            width: 100%;
            border-collapse: collapse;
            margin: 20px 0;
        }
        table, th, td {
            border: 1px solid black;
        }
        th, td {
            padding: 10px;
            text-align: center;
        }
        .result {
            margin-top: 20px;
            font-weight: bold;
        }
    </style>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/xlsx/0.18.5/xlsx.full.min.js"></script>
</head>
<body>
    <h1>Cálculo do Risco Familiar</h1>
    <form id="riskForm">
        <div>
            <label for="nomeAcs">NOME DO ACS:</label>
            <input type="text" id="nomeAcs">
        </div>
        <div>
            <label for="equipe">EQUIPE:</label>
            <input type="text" id="equipe">
        </div>
        <br>
        <table>
            <thead>
                <tr>
                    <th>Nome do Morador</th>
                    <th>CNS/CPF</th>
                    <th>Acamado</th>
                    <th>Deficiência Física</th>
                    <th>Deficiência Mental</th>
                    <th>Baixas Condições de Saneamento</th>
                    <th>Desnutrição Grave</th>
                    <th>Drogadição</th>
                    <th>Desemprego</th>
                    <th>Analfabetismo</th>
                    <th>Menor de 6 meses</th>
                    <th>Maior de 70 anos</th>
                    <th>Hipertensão Arterial Sistêmica</th>
                    <th>Diabetes Mellitus</th>
                    <th>Relação Morador/Cômodo</th>
                    <th>Escore Total</th>
                    <th>Classificação do Risco Familiar</th>
                </tr>
            </thead>
            <tbody id="tableBody">
                <!-- Gerar automaticamente 13 linhas -->
            </tbody>
        </table>
        <button type="button" onclick="adicionarLinhas()">Adicionar 12 Linhas</button>
        <button type="button" onclick="calcularRisco()">Calcular Risco</button>
        <button type="button" onclick="salvarPlanilha()">Salvar em Planilha</button>
    </form>
    <div class="result">
        <p><strong>Escore Total:</strong> <span id="escoreTotal">0</span></p>
        <p><strong>Classificação do Risco Familiar:</strong> <span id="classificacaoRisco"></span></p>
    </div>
    <script>
        const tableBody = document.getElementById('tableBody');

        function adicionarLinhas() {
            for (let i = 0; i < 12; i++) {
                const tr = document.createElement('tr');

                // Adicionando campos à linha
                tr.innerHTML = `
                    <td><input type="text" class="nome-morador"></td>
                    <td><input type="text" class="cnsCpf"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Acamado" data-value="3"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Deficiência Física" data-value="3"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Deficiência Mental" data-value="3"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Baixas Condições de Saneamento" data-value="3"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Desnutrição Grave" data-value="3"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Drogadição" data-value="2"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Desemprego" data-value="2"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Analfabetismo" data-value="1"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Menor de 6 meses" data-value="1"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Maior de 70 anos" data-value="1"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Hipertensão Arterial Sistêmica" data-value="1"></td>
                    <td><input type="checkbox" class="risk-factor" data-name="Diabetes Mellitus" data-value="1"></td>
                    <td>
                        <select class="relationFactor">
                            <option value="3">Maior que 1 (3 pontos)</option>
                            <option value="2">Igual a 1 (2 pontos)</option>
                            <option value="0">Menor que 1 (0 ponto)</option>
                        </select>
                    </td>
                    <td class="escoreTotal">0</td>
                    <td class="classificacaoRisco"></td>
                `;
                tableBody.appendChild(tr);
            }
        }

        function salvarPlanilha() {
            // Aqui você adiciona as funcionalidades para salvar os dados em uma planilha
        }
    </script>
</body>
</html>
