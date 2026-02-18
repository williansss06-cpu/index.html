<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>Global Acessórios — Calculadora de Retorno</title>

<!-- Font + Chart -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>

<style>
  :root {
    --azul:#004aad;
    --azul2:#022e70;
    --bg-card:#f4f6f9;
    --texto:#0f172a;
    --muted:#5b6475;
    --radius:16px;
    --shadow:0 10px 30px rgba(0,0,0,.08);
  }

  * { box-sizing:border-box; }
  body {
    margin:0;
    font-family:Inter, Arial, sans-serif;
    background:#fff;
    color:var(--texto);
  }

  header {
    background:linear-gradient(120deg,var(--azul),var(--azul2));
    color:#fff;
    padding:30px 20px;
    text-align:center;
  }
  header img {
    height:52px;
    object-fit:contain;
    filter:drop-shadow(0 2px 4px rgba(0,0,0,.4));
  }
  header h1 {
    margin:12px 0 4px;
    font-size:clamp(20px,2vw,26px);
    font-weight:600;
  }
  header .subtitle {
    margin:0;
    font-size:14px;
    opacity:.95;
    font-weight:400;
  }

  .wrap {
    max-width:1080px;
    margin:0 auto;
    padding:20px 16px 40px;
  }

  .card {
    background:var(--bg-card);
    border-radius:var(--radius);
    padding:20px;
    margin:16px 0;
    box-shadow:var(--shadow);
  }

  .section-title {
    font-size:16px;
    font-weight:600;
    margin:0 0 12px;
    color:#0f172a;
    display:flex;
    align-items:center;
    gap:8px;
  }

  .section-title span.tag {
    background:#e6ecfb;
    color:#0b1a38;
    font-size:11px;
    font-weight:600;
    padding:3px 8px;
    border-radius:999px;
  }

  label {
    display:block;
    font-weight:600;
    color:#2d3648;
    font-size:13px;
    margin-bottom:4px;
  }

  input {
    width:100%;
    padding:10px;
    border-radius:10px;
    border:1px solid #ccd3e0;
    background:#fff;
    font-size:15px;
    margin-bottom:12px;
  }

  input:focus {
    outline:none;
    border-color:var(--azul);
    box-shadow:0 0 0 3px rgba(0,74,173,.2);
  }

  .grid-2 {
    display:grid;
    gap:12px;
  }
  @media(min-width:680px){
    .grid-2{
      grid-template-columns:1fr 1fr;
    }
  }

  button#btnCalcular {
    background:var(--azul);
    color:#fff;
    border:none;
    padding:12px 18px;
    border-radius:12px;
    cursor:pointer;
    font-weight:700;
    font-size:15px;
  }
  button#btnCalcular:hover {
    background:var(--azul2);
  }

  .kpis {
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
    gap:12px;
    margin-top:10px;
  }
  .kpi {
    background:#fff;
    border:1px solid #e6e9f2;
    border-radius:12px;
    padding:14px;
    text-align:center;
  }
  .kpi .label {
    font-size:12px;
    color:var(--muted);
    font-weight:500;
  }
  .kpi .value {
    font-size:18px;
    font-weight:800;
    color:var(--azul);
    margin-top:4px;
    min-height:24px;
  }

  .success {
    display:none;
    background:#e8fff1;
    color:#055f2c;
    border:1px solid #12a97e33;
    border-radius:10px;
    padding:12px 14px;
    font-size:13px;
    font-weight:500;
    margin-top:16px;
  }

  canvas {
    width:100%;
    max-height:320px;
    margin-top:20px;
  }

  .actions-row {
    display:flex;
    gap:10px;
    flex-wrap:wrap;
    margin-top:16px;
  }
  a.btnWhats {
    background:#e6ecfb;
    color:#0b1a38;
    padding:12px 18px;
    border-radius:12px;
    font-weight:700;
    text-decoration:none;
    display:inline-block;
  }

  footer {
    text-align:center;
    color:#6c7890;
    font-size:12px;
    padding:24px 16px 40px;
  }
</style>
</head>
<body>

<header>
  <!-- Substitua o src abaixo pelo caminho do seu logo (logo.png) -->
  <img src="logo.png" alt="Global Acessórios">
  <h1>Calculadora de Retorno — Cintas de Amarração</h1>
  <p class="subtitle">
    Preencha seus dados e simule o retorno financeiro e sustentável da substituição do stretch por cintas reutilizáveis.
  </p>
</header>

<main class="wrap">

  <!-- BLOCO ÚNICO DE ENTRADA -->
  <section class="card">
    <h2 class="section-title">
      1) Seus dados e cenário de operação
      <span class="tag">obrigatório</span>
    </h2>

    <!-- Dados do cliente -->
    <div class="grid-2">
      <div>
        <label>Nome *</label>
        <input type="text" id="nome" placeholder="Seu nome">
      </div>
      <div>
        <label>Empresa *</label>
        <input type="text" id="empresa" placeholder="Sua empresa">
      </div>
    </div>

    <div class="grid-2">
      <div>
        <label>E-mail corporativo *</label>
        <input type="email" id="email" placeholder="voce@empresa.com">
      </div>
      <div>
        <label>Telefone / WhatsApp *</label>
        <input type="tel" id="telefone" placeholder="(11) 96191-8898">
      </div>
    </div>

    <!-- Dados operacionais -->
    <div class="grid-2">
      <div>
        <label>Quantidade média de pallets *</label>
        <input type="number" id="pallets" placeholder="Ex.: 2000">
      </div>
      <div>
        <label>Giro de estoque (movimentações/mês) *</label>
        <input type="number" id="giro" placeholder="Ex.: 4">
      </div>
    </div>

    <div class="grid-2">
      <div>
        <label>Peso de stretch por pallet (g) *</label>
        <input type="number" id="peso_g" placeholder="Ex.: 800">
      </div>
      <div>
        <label>Preço do kg de stretch (R$) *</label>
        <input type="number" id="precoKg" placeholder="Ex.: 17.5" step="0.01">
      </div>
    </div>

    <div style="font-size:12px;color:#5b6475;line-height:1.4;">
      Vida útil estimada da cinta: 5 anos (60 meses).<br>
      Cada pallet usa 2 cintas reutilizáveis (preço interno da cinta já considerado).
    </div>

    <div style="margin-top:16px;">
      <button id="btnCalcular">Calcular retorno</button>
    </div>

    <div id="msgErro" style="color:#b91c1c;font-size:13px;font-weight:500;margin-top:10px;display:none;">
      ⚠️ Preencha todos os campos obrigatórios antes de calcular.
    </div>

    <div id="msgOk" class="success">
      ✅ Simulação concluída! Nossa equipe entrará em contato com você em breve.
    </div>
  </section>

  <!-- RESULTADO -->
  <section class="card">
    <h2 class="section-title">
      2) Resultado financeiro
      <span class="tag">payback & ROI</span>
    </h2>

    <div class="kpis">
      <div class="kpi">
        <div class="label">Custo mensal (stretch)</div>
        <div class="value" id="kCustoMensal">—</div>
      </div>
      <div class="kpi">
        <div class="label">Investimento em cintas</div>
        <div class="value" id="kInvest">—</div>
      </div>
      <div class="kpi">
        <div class="label">Economia mensal</div>
        <div class="value" id="kEconMensal">—</div>
      </div>
      <div class="kpi">
        <div class="label">Economia total (5 anos)</div>
        <div class="value" id="kEconTotal">—</div>
      </div>
      <div class="kpi">
        <div class="label">Payback</div>
        <div class="value" id="kPayback">—</div>
      </div>
      <div class="kpi">
        <div class="label">ROI (5 anos)</div>
        <div class="value" id="kROI">—</div>
      </div>
    </div>

    <canvas id="grafico"></canvas>

    <div class="actions-row">
      <a id="zapLink" href="#" target="_blank" rel="noopener" class="btnWhats">
        💬 Falar com um consultor
      </a>
    </div>
  </section>
</main>

<footer>
  © <span id="year"></span> Global Acessórios. Todos os direitos reservados.
</footer>

<script>
  // CONFIG INTERNAS
  const PRECO_CINTA = 16.5;                // R$ por cinta (interno)
  const CINTAS_POR_PALLET = 2;             // fixo
  const FORM_EMAIL = "globalacessoriosemgeral@gmail.com";
  const WHATSAPP = "5511961918898";

  const BRL = new Intl.NumberFormat('pt-BR',{style:'currency',currency:'BRL'});

  let chartRef = null;

  function getVal(id){
    const el = document.getElementById(id);
    if(!el) return "";
    return (el.value || "").trim();
  }

  function getNum(id){
    const v = getVal(id).replace(",", ".");
    const n = parseFloat(v);
    return isNaN(n) ? 0 : n;
  }

  function validarCamposObrigatorios(){
    const obrigatorios = ["nome","empresa","email","telefone","pallets","giro","peso_g","precoKg"];
    for (const id of obrigatorios){
      if(!getVal(id)){
        return false;
      }
    }
    return true;
  }

  function calcularCenarios(){
    // Entradas
    const pallets = getNum("pallets");
    const giro = getNum("giro");
    const peso_g = getNum("peso_g"); // gramas por pallet
    const precoKg = getNum("precoKg"); // R$/kg

    // custo mensal stretch = pallets × giro × peso (g) × (preçoKg ÷ 1000)
    const custoMensalStretch = pallets * giro * peso_g * (precoKg / 1000);

    // investimento em cintas = pallets × CINTAS_POR_PALLET × PRECO_CINTA
    const investimentoCintas = pallets * CINTAS_POR_PALLET * PRECO_CINTA;

    // economia mensal = custo do stretch mensal que deixa de existir
    const economiaMensal = custoMensalStretch;

    // economia total em 5 anos (60 meses)
    const economiaTotal5Anos = economiaMensal * 60;

    // payback (meses)
    const payback = economiaMensal > 0 ? (investimentoCintas / economiaMensal) : Infinity;

    // ROI 5 anos
    const roi = investimentoCintas > 0
      ? ((economiaTotal5Anos - investimentoCintas) / investimentoCintas) * 100
      : 0;

    // Atualiza KPIs
    document.getElementById("kCustoMensal").textContent = BRL.format(custoMensalStretch);
    document.getElementById("kInvest").textContent        = BRL.format(investimentoCintas);
    document.getElementById("kEconMensal").textContent    = BRL.format(economiaMensal);
    document.getElementById("kEconTotal").textContent     = BRL.format(economiaTotal5Anos);
    document.getElementById("kPayback").textContent       = (isFinite(payback) ? payback.toFixed(1).replace(".",",") : "N/A") + " meses";
    document.getElementById("kROI").textContent           = (isFinite(roi) ? roi.toFixed(1).replace(".",",") : "N/A") + "%";

    // Mensagem de sucesso
    document.getElementById("msgOk").style.display = "block";

    // WhatsApp resumo
    const resumoWhats =
      "Simulação Global Acessórios%0A" +
      "Nome: " + encodeURIComponent(getVal("nome")) + "%0A" +
      "Empresa: " + encodeURIComponent(getVal("empresa")) + "%0A" +
      "Telefone: " + encodeURIComponent(getVal("telefone")) + "%0A" +
      "---%0A" +
      "Pallets: " + pallets + "%0A" +
      "Giro/mês: " + giro + "%0A" +
      "Peso stretch (g/pallet): " + peso_g + "%0A" +
      "Preço kg stretch: R$ " + precoKg + "%0A" +
      "---%0A" +
      "Custo mensal (stretch): " + encodeURIComponent(BRL.format(custoMensalStretch)) + "%0A" +
      "Investimento (cintas): " + encodeURIComponent(BRL.format(investimentoCintas)) + "%0A" +
      "Economia mensal: " + encodeURIComponent(BRL.format(economiaMensal)) + "%0A" +
      "Economia 5 anos: " + encodeURIComponent(BRL.format(economiaTotal5Anos)) + "%0A" +
      "Payback: " + (isFinite(payback) ? payback.toFixed(1).replace(".",",") + " meses" : "N/A") + "%0A" +
      "ROI 5 anos: " + (isFinite(roi) ? roi.toFixed(1).replace(".",",") + "%" : "N/A");

    document.getElementById("zapLink").href =
      "https://wa.me/" + WHATSAPP + "?text=" + resumoWhats;

    // Gráfico de economia acumulada (60 meses)
    const meses = Array.from({length:60}, (_,i)=> i+1);
    const curva = meses.map(m => economiaMensal * m);

    const ctx = document.getElementById("grafico").getContext("2d");
    if(chartRef){ chartRef.destroy(); }
    chartRef = new Chart(ctx, {
      type:'line',
      data:{
        labels: meses.map(m=>"M"+m),
        datasets:[{
          label:'Economia acumulada (R$)',
          data: curva,
          borderColor:'#004aad',
          backgroundColor:'rgba(0,74,173,0.12)',
          fill:true,
          tension:0.25
        }]
      },
      options:{
        plugins:{ legend:{display:false} },
        scales:{ y:{ beginAtZero:true } }
      }
    });

    // envio automático por e-mail via FormSubmit
    enviarEmailLead({
      nome: getVal("nome"),
      empresa: getVal("empresa"),
      email: getVal("email"),
      telefone: getVal("telefone"),
      pallets,
      giro,
      peso_g,
      precoKg,
      custoMensalStretch,
      investimentoCintas,
      economiaMensal,
      economiaTotal5Anos,
      payback,
      roi
    });
  }

  async function enviarEmailLead(payload){
    // Monta form invisível e envia via POST para FormSubmit
    // Isso dispara o e-mail pra você automaticamente.
    const form = document.createElement("form");
    form.action = "https://formsubmit.co/" + encodeURIComponent(FORM_EMAIL);
    form.method = "POST";
    form.style.display = "none";

    const hidden = {
      "_subject": "📊 Nova simulação enviada — Calculadora Global Acessórios",
      "_captcha": "false",
      "_template": "table",
      "Nome": payload.nome,
      "Empresa": payload.empresa,
      "E-mail": payload.email,
      "Telefone": payload.telefone,
      "Qtd pallets": payload.pallets,
      "Giro/mês": payload.giro,
      "Peso stretch (g/pallet)": payload.peso_g,
      "Preço kg stretch (R$)": payload.precoKg,
      "Cintas por pallet (fixo)": CINTAS_POR_PALLET,
      "Preço cinta (fixo R$)": PRECO_CINTA,
      "Custo mensal stretch (R$)": payload.custoMensalStretch.toFixed(2),
      "Investimento cintas (R$)": payload.investimentoCintas.toFixed(2),
      "Economia mensal (R$)": payload.economiaMensal.toFixed(2),
      "Economia 5 anos (R$)": payload.economiaTotal5Anos.toFixed(2),
      "Payback (meses)": isFinite(payload.payback) ? payload.payback.toFixed(2) : "N/A",
      "ROI 5 anos (%)": isFinite(payload.roi) ? payload.roi.toFixed(2) : "N/A"
    };

    for(const [key,val] of Object.entries(hidden)){
      const inp = document.createElement("input");
      inp.type = "hidden";
      inp.name = key;
      inp.value = val;
      form.appendChild(inp);
    }

    document.body.appendChild(form);
    form.submit();
  }

  document.getElementById("btnCalcular").addEventListener("click", (e)=>{
    e.preventDefault();
    document.getElementById("msgOk").style.display = "none";
    document.getElementById("msgErro").style.display = "none";

    if(!validarCamposObrigatorios()){
      document.getElementById("msgErro").style.display = "block";
      return;
    }

    calcularCenarios();
  });

  document.getElementById("year").textContent = new Date().getFullYear();
</script>

</body>
</html>
