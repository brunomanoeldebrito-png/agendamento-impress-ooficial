<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Impressão Rápida</title>
  <style>
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
      h1 {
  background-color: transparent !important;
  color: #222 !important; /* muda também a cor do texto, se necessário */
}

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
  </style>
</head>
<body>
  <div class="container">
    <h1>Impressão Rápida</h1>
    <h2>Impressão Rápida</h2>


    <h3>Agendamento Online</h3>
    <h3>Tabela de Serviços e Preços</h3>
    <table>
      <thead>
        <tr>
          <th>Serviço</th>
          <th>Descrição</th>
          <th>Preço</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Xerox</td>
          <td>Preto e branco</td>
          <td>R$ 2,00</td>
        </tr>
        <tr>
          <td>Impressão</td>
          <td>comum preto e branco</td>
          <td>R$ 2,50</td>
        </tr>
      </tbody>
    </table>
    <h4>observação:Se escolhe a opção:impressão la no final vai ter uma opção so para quem escolheu essa opção:envia pdf, peço que logo apos manda o resumo no whatsapp, peço que mande o pdf tabem. </h4>
    <form id="agendamentoForm">
      <!-- Etapa 1 -->
      <div id="etapa-servico">
        <label for="servico">Serviço:</label>
        <select id="servico" name="servico" required>
          <option value="">Selecione</option>
          <option value="Xerox">Xerox (preto e branco)</option>
          <option value="Impressao">Impressão comum</option>
        </select>
        <button type="button" id="btnProximoServico">Próximo</button>
      </div>

      <!-- Etapa 2 -->
      <div id="etapa-data" class="hidden">
        <h2>Escolha uma Data</h2>
        <table id="tabela-datas"></table>
        <button type="button" id="btnProximoData">Próximo</button>
      </div>

      <!-- Etapa 3 -->
      <div id="etapa-horario" class="hidden">
        <h2>Escolha um Horário</h2>
        <table id="tabela-horarios"></table>
        <button type="button" id="btnProximoHorario">Próximo</button>
      </div>

      <!-- Etapa 4 -->
      <div id="etapa-info" class="hidden">
        <label for="nome">Seu nome:</label>
        <input type="text" id="nome" name="nome" required />

        <label for="quantidade">Quantidade de páginas:</label>
        <input type="number" id="quantidade" name="quantidade" min="1" required />

        <label for="contato">WhatsApp ou E-mail:</label>
        <input type="text" id="contato" name="contato" placeholder="Ex: 719XXXXXXX ou email@exemplo.com" required />

        <label for="formaPagamento">Forma de pagamento:</label>
        <input type="text" id="formaPagamento" name="formaPagamento" placeholder="No atendimento, PIX, etc." />

        <div id="opcaoPDF" class="hidden">
          <label for="arquivoPDF">Enviar PDF:</label>
          <input type="file" id="arquivoPDF" name="arquivoPDF" accept=".pdf" />
        </div>

        <button type="submit">📩 Enviar Agendamento</button>
      </div>
    </form>
  </div>

  <script>
    const agendamentoForm = document.getElementById('agendamentoForm');
    const etapaServico = document.getElementById('etapa-servico');
    const etapaData = document.getElementById('etapa-data');
    const etapaHorario = document.getElementById('etapa-horario');
    const etapaInfo = document.getElementById('etapa-info');
    const opcaoPDF = document.getElementById('opcaoPDF');

    let servicoSelecionado = '';
    let dataSelecionada = '';
    let horarioSelecionado = '';

    const horariosPadrao = ['08:00','09:00','10:00','11:00','12:00','13:00','14:00','15:00','16:00','17:00','18:00','19:00','20:00','21:00'];
    const horariosBloqueados = {};
    const datasBloqueadas = [];

    function criarTabelaDatas() {
      const tabela = document.getElementById('tabela-datas');
      tabela.innerHTML = '<tr><th>Data</th></tr>';
      const hoje = new Date();
      for(let i = 0; i < 7; i++) {
        const d = new Date();
        d.setDate(hoje.getDate() + i);
        const dia = d.toISOString().split('T')[0];
        if (!datasBloqueadas.includes(dia)) {
          const tr = document.createElement('tr');
          tr.innerHTML = `<td><button type="button" class="btnData" data-date="${dia}">${dia}</button></td>`;
          tabela.appendChild(tr);
        }
      }
    }

    function criarTabelaHorarios(data) {
      const tabela = document.getElementById('tabela-horarios');
      tabela.innerHTML = '<tr><th>Horário</th></tr>';
      let diaSemana = new Date(data).getDay();
      horariosPadrao.forEach(h => {
        if (diaSemana >= 1 && diaSemana <= 5 && parseInt(h.split(':')[0]) >= 12 && parseInt(h.split(':')[0]) <= 17) return;
        if (horariosBloqueados[data] && horariosBloqueados[data].includes(h)) return;
        const tr = document.createElement('tr');
        tr.innerHTML = `<td><button type="button" class="btnHorario" data-horario="${h}">${h}</button></td>`;
        tabela.appendChild(tr);
      });
    }

    document.getElementById('btnProximoServico').addEventListener('click', () => {
      servicoSelecionado = document.getElementById('servico').value;
      if (!servicoSelecionado) return alert('Selecione um serviço');
      etapaServico.classList.add('hidden');
      etapaData.classList.remove('hidden');
      if (servicoSelecionado === 'Impressao') opcaoPDF.classList.remove('hidden');
      criarTabelaDatas();
    });

    document.getElementById('tabela-datas').addEventListener('click', e => {
      if (e.target.classList.contains('btnData')) {
        dataSelecionada = e.target.dataset.date;
        document.querySelectorAll('.btnData').forEach(btn => btn.style.background = '');
        e.target.style.background = '#28a745';
      }
    });

    document.getElementById('btnProximoData').addEventListener('click', () => {
      if (!dataSelecionada) return alert('Selecione uma data');
      etapaData.classList.add('hidden');
      etapaHorario.classList.remove('hidden');
      criarTabelaHorarios(dataSelecionada);
    });

    document.getElementById('tabela-horarios').addEventListener('click', e => {
      if (e.target.classList.contains('btnHorario')) {
        horarioSelecionado = e.target.dataset.horario;
        document.querySelectorAll('.btnHorario').forEach(btn => btn.style.background = '');
        e.target.style.background = '#28a745';
      }
    });

    document.getElementById('btnProximoHorario').addEventListener('click', () => {
      if (!horarioSelecionado) return alert('Selecione um horário');
      etapaHorario.classList.add('hidden');
      etapaInfo.classList.remove('hidden');
    });

    agendamentoForm.addEventListener('submit', function (e) {
      e.preventDefault();
      const nome = document.getElementById('nome').value;
      const quantidade = document.getElementById('quantidade').value;
      const contato = document.getElementById('contato').value;
      const formaPagamento = document.getElementById('formaPagamento').value || "No atendimento";

      const mensagem = `📋 *Novo Agendamento - Impressão Rápida*%0A👤 *Nome:* ${nome}%0A🛠️ *Serviço:* ${servicoSelecionado}%0A📄 *Quantidade:* ${quantidade} páginas%0A📅 *Data:* ${dataSelecionada}%0A⏰ *Horário:* ${horarioSelecionado}%0A📞 *Contato:* ${contato}%0A💳 *Pagamento:* ${formaPagamento}`;
      const numero = "5571982513027";
      const url = `https://wa.me/${numero}?text=${mensagem}`;
      window.open(url, '_blank');
      agendamentoForm.reset();
      location.reload();
    });
  </script>
</body>
</html>




