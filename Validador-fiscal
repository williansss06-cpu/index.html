<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1"/>
  <title>Validação Automática de Notas</title>
  <style>
    :root{
      --orange:#d86f00;
      --orange2:#f28c1b;
      --bg:#f2f3f5;
      --card:#ffffff;
      --text:#1f2937;
      --muted:#6b7280;
      --line:#e5e7eb;
      --ok:#16a34a;
      --warn:#f59e0b;
      --err:#dc2626;
      --shadow: 0 10px 25px rgba(0,0,0,.08);
      --radius:18px;
      --radius2:14px;
      --font: system-ui, -apple-system, Segoe UI, Roboto, Helvetica, Arial, "Apple Color Emoji","Segoe UI Emoji";
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family:var(--font);
      color:var(--text);
      background:var(--bg);
    }

    /* Header */
    .topbar{
      display:flex;
      align-items:center;
      gap:18px;
      padding:16px 20px;
      background:#fff;
      border-bottom:1px solid var(--line);
    }
    .logo{
      width:120px;
      height:80px;
      border-radius:16px;
      display:flex;
      align-items:center;
      justify-content:center;
      background:#fff;
      border:1px solid var(--line);
      overflow:hidden;
    }
    .logo svg{width:86px;height:86px}
    .titlewrap{
      flex:1;
      min-width:240px;
    }
    .titlewrap h1{
      margin:0;
      font-size:26px;
      letter-spacing:.2px;
      font-weight:800;
    }
    .titlewrap .sub{
      margin-top:4px;
      color:var(--muted);
      font-size:13px;
    }

    /* Orange band */
    .band{
      background:linear-gradient(90deg, var(--orange) 0%, var(--orange2) 100%);
      padding:18px 0 26px 0;
    }

    .container{
      max-width:1180px;
      margin:0 auto;
      padding:0 16px 28px;
    }

    /* Main white panel */
    .panel{
      background:var(--card);
      border-radius:22px;
      box-shadow:var(--shadow);
      padding:18px 18px 16px;
      border:1px solid rgba(255,255,255,.35);
      margin-top:-28px;
    }

    /* Buttons row */
    .btnrow{
      display:flex;
      flex-wrap:wrap;
      gap:12px;
      align-items:center;
      margin:6px 0 14px;
    }
    .btn{
      border:2px solid var(--orange2);
      background:#fff;
      color:var(--orange);
      padding:12px 14px;
      border-radius:14px;
      font-weight:800;
      cursor:pointer;
      display:inline-flex;
      align-items:center;
      gap:10px;
      user-select:none;
      box-shadow:0 6px 16px rgba(216,111,0,.08);
      transition:.15s ease;
      min-height:48px;
    }
    .btn:hover{transform:translateY(-1px)}
    .btn:active{transform:translateY(0)}
    .btn.primary{
      background:var(--orange);
      color:#fff;
      border-color:var(--orange);
    }
    .btn.ghost{
      border-color:#cbd5e1;
      color:#111827;
    }

    /* Grid blocks */
    .grid{
      display:grid;
      grid-template-columns: 1.2fr 1fr;
      gap:16px;
      margin-top:10px;
    }
    @media (max-width: 980px){
      .grid{grid-template-columns:1fr}
    }

    .card{
      background:#fff;
      border:1px solid var(--line);
      border-radius:18px;
      padding:14px 14px 12px;
      box-shadow:0 8px 20px rgba(0,0,0,.05);
    }
    .card h2{
      margin:0 0 10px 0;
      font-size:16px;
      display:flex;
      align-items:center;
      gap:10px;
      font-weight:900;
    }

    .fields{
      display:grid;
      grid-template-columns:1fr 1fr;
      gap:10px;
    }
    @media (max-width: 700px){
      .fields{grid-template-columns:1fr}
    }
    .field label{
      display:block;
      font-size:12px;
      color:var(--muted);
      margin:0 0 6px 2px;
      font-weight:700;
    }
    .field input, .field textarea{
      width:100%;
      padding:11px 12px;
      border:1px solid var(--line);
      border-radius:12px;
      outline:none;
      font-size:14px;
      background:#fbfbfc;
    }
    .field textarea{
      min-height:120px;
      resize:vertical;
      background:#fff;
    }
    .field input[readonly]{color:#111827}
    .hint{
      margin-top:8px;
      font-size:12px;
      color:var(--muted);
    }

    /* File inputs */
    .filegrid{
      display:grid;
      grid-template-columns:1fr 1fr;
      gap:12px;
      margin-top:8px;
    }
    @media (max-width: 800px){
      .filegrid{grid-template-columns:1fr}
    }
    .filebox{
      border:1px dashed #d1d5db;
      border-radius:14px;
      padding:12px;
      background:#fff;
    }
    .filebox .top{
      display:flex;justify-content:space-between;align-items:center;gap:10px;
      margin-bottom:8px;
    }
    .badge{
      font-size:11px;
      padding:4px 8px;
      border-radius:999px;
      border:1px solid var(--line);
      color:#111827;
      background:#f8fafc;
      font-weight:800;
    }
    .filebox .name{
      font-size:12px;color:var(--muted);
      white-space:nowrap;overflow:hidden;text-overflow:ellipsis;
      margin-top:6px;
    }

    /* Rules table */
    table{
      width:100%;
      border-collapse:collapse;
      border-radius:14px;
      overflow:hidden;
      border:1px solid var(--line);
    }
    thead th{
      text-align:left;
      font-size:12px;
      color:#111827;
      background:#f9fafb;
      padding:10px 10px;
      border-bottom:1px solid var(--line);
      font-weight:900;
    }
    tbody td{
      padding:11px 10px;
      border-bottom:1px solid var(--line);
      vertical-align:top;
      font-size:13px;
    }
    tbody tr:last-child td{border-bottom:none}
    .pill{
      display:inline-flex;
      align-items:center;
      justify-content:center;
      min-width:64px;
      padding:6px 10px;
      border-radius:999px;
      font-weight:900;
      font-size:12px;
      border:1px solid transparent;
    }
    .pill.ok{background:rgba(22,163,74,.08); color:var(--ok); border-color:rgba(22,163,74,.18)}
    .pill.warn{background:rgba(245,158,11,.10); color:var(--warn); border-color:rgba(245,158,11,.18)}
    .pill.err{background:rgba(220,38,38,.08); color:var(--err); border-color:rgba(220,38,38,.18)}

    /* Message box */
    .resultHeader{
      display:flex;
      align-items:center;
      gap:10px;
      margin-bottom:10px;
    }
    .resultBig{
      display:inline-flex;
      align-items:center;
      gap:8px;
      font-weight:1000;
      padding:10px 14px;
      border-radius:999px;
      border:2px solid rgba(220,38,38,.25);
      background:rgba(220,38,38,.06);
      color:var(--err);
    }
    .resultBig.ok{
      border-color:rgba(22,163,74,.25);
      background:rgba(22,163,74,.08);
      color:var(--ok);
    }

    .miniRow{
      display:flex;
      gap:10px;
      flex-wrap:wrap;
      margin-top:10px;
      color:var(--muted);
      font-size:12px;
      font-weight:700;
    }
    .miniRow span{background:#f8fafc;border:1px solid var(--line);padding:6px 10px;border-radius:999px}

    .sep{
      height:1px;background:var(--line);margin:14px 0;
    }

    .footerNote{
      font-size:12px;
      color:var(--muted);
      margin-top:10px;
    }
  </style>
</head>

<body>
  <div class="topbar">
    <div class="logo" title="Mundial Logistics Group">
      <!-- Simple inline logo placeholder (no external file) -->
      <svg viewBox="0 0 120 120" aria-hidden="true">
        <defs>
          <linearGradient id="g" x1="0" x2="1">
            <stop offset="0" stop-color="#d86f00"/>
            <stop offset="1" stop-color="#f28c1b"/>
          </linearGradient>
        </defs>
        <circle cx="60" cy="60" r="52" fill="none" stroke="url(#g)" stroke-width="10"/>
        <text x="60" y="58" font-size="18" text-anchor="middle" font-family="Arial" font-weight="800" fill="#111">mundial</text>
        <text x="60" y="76" font-size="12" text-anchor="middle" font-family="Arial" font-weight="700" fill="#6b7280">Logistics Group</text>
      </svg>
    </div>

    <div class="titlewrap">
      <h1>Validação Automática de Notas</h1>
      <div class="sub">Importar XML Remessa + XML Venda • Validar regras fiscais e consistência (quantidade/valor)</div>
    </div>
  </div>

  <div class="band">
    <div class="container">
      <div class="panel">

        <div class="btnrow">
          <button class="btn" id="btnPickRemessa">📥 Importar XML Remessa</button>
          <button class="btn" id="btnPickVenda">📥 Importar XML Venda</button>

          <button class="btn" id="btnPickDepositantes">📄 Importar depositantes (CSV/TXT)</button>

          <button class="btn primary" id="btnValidar">✅ Validar</button>
          <button class="btn ghost" id="btnExport">📊 Exportar relatório (CSV)</button>
          <button class="btn ghost" id="btnLimpar">🧹 Limpar</button>

          <input type="file" id="fileRemessa" accept=".xml" style="display:none" />
          <input type="file" id="fileVenda" accept=".xml" style="display:none" />
          <input type="file" id="fileDepositantes" accept=".csv,.txt" style="display:none" />
        </div>

        <div class="card">
          <h2>📦 Importar XMLs</h2>

          <div class="filegrid">
            <div class="filebox">
              <div class="top">
                <div style="font-weight:1000">XML Remessa</div>
                <span class="badge" id="badgeRemessa">não carregado</span>
              </div>
              <div class="name" id="nameRemessa">—</div>
            </div>

            <div class="filebox">
              <div class="top">
                <div style="font-weight:1000">XML Venda</div>
                <span class="badge" id="badgeVenda">não carregado</span>
              </div>
              <div class="name" id="nameVenda">—</div>
            </div>
          </div>

          <div class="miniRow">
            <span id="infoDepositantes">Depositantes carregados: 0</span>
            <span id="infoChave">Chave Remessa: —</span>
            <span id="infoNF">NF Remessa: — • NF Venda: —</span>
          </div>
        </div>

        <div class="sep"></div>

        <div class="grid">
          <!-- Left: Rules -->
          <div class="card">
            <h2>📋 Regras e validações</h2>
            <table>
              <thead>
                <tr>
                  <th style="width:40%">Regra</th>
                  <th style="width:14%">Status</th>
                  <th>Detalhe</th>
                </tr>
              </thead>
              <tbody id="rulesBody">
                <!-- Filled by JS -->
              </tbody>
            </table>

            <div class="footerNote">
              Observação: “Endereço” aqui é referência fixa da base Mundial. A validação prática é por <b>CEP + Bairro</b>.
            </div>
          </div>

          <!-- Right: Message -->
          <div class="card">
            <h2>🧾 Mensagem ao fornecedor</h2>

            <div class="resultHeader">
              <div id="resultadoBig" class="resultBig">❌ REPROVADO</div>
            </div>

            <div class="field">
              <label>Mensagem pronta (copiar e enviar)</label>
              <textarea id="msgFornecedor" placeholder="A mensagem aparecerá aqui após validar..."></textarea>
              <div class="hint">Dica: a mensagem já sai com os itens que precisam de ajuste.</div>
            </div>

            <div class="sep"></div>

            <div class="fields">
              <div class="field">
                <label>CNPJ Mundial (esperado na Remessa)</label>
                <input id="cnpjMundial" readonly />
              </div>

              <div class="field">
                <label>Endereço (referência — Base Mundial)</label>
                <input id="enderecoBase" readonly />
              </div>

              <div class="field">
                <label>CEP aceito (Remessa)</label>
                <input id="cepAceito" readonly />
              </div>

              <div class="field">
                <label>Bairros aceitos (Remessa)</label>
                <input id="bairrosAceitos" readonly />
              </div>

              <div class="field">
                <label>Status geral</label>
                <input id="statusGeral" readonly value="Aguardando validação" />
              </div>

              <div class="field">
                <label>Depositante (Venda) — dest/CNPJ</label>
                <input id="depositanteVenda" readonly value="—" />
              </div>

              <div class="field" style="grid-column:1/-1">
                <label>Natureza Remessa / Natureza Venda (lidas do XML)</label>
                <input id="natOps" readonly value="—" />
              </div>
            </div>
          </div>
        </div>

      </div><!-- panel -->
    </div><!-- container -->
  </div><!-- band -->

<script>
/* =========================
   CONFIG (regras fixas)
========================= */
const CFG = {
  CNPJ_MUNDIAL: "05.075.152/0001-77",
  ENDERECO_BASE: "ESTRADA VELHA GUARULHOS SÃO MIGUEL, 1971",
  CEP_ACEITO: "07210-250",
  BAIRROS_ACEITOS: ["JARDIM ARAPONGAS", "JARDIM CUMBICA"],

  // CFOP permitidos (por item)
  CFOP_PERMITIDOS: ["5949","6649","5923","6923"],

  // CST/CSOSN permitidos (3 dígitos)
  CST_CSOSN_PERMITIDOS: ["040","041","090"],

  // Art.129 condicional (se houver CFOP 5923/6923, exige texto "ART.129")
  CFOP_ART129: ["5923","6923"],

  // Natureza: Remessa aceita se iniciar com REM / OUTRAS / SIMPLES (cobre abreviações)
  REMESSA_PREFIXOS_OK: ["REM", "OUTRAS", "SIMPLES"],

  // Venda aceita se iniciar com VENDA ou REVENDA
  VENDA_PREFIXOS_OK: ["VENDA", "REVENDA"],

  // Comparação de valores (tolerância)
  TOLERANCIA_VALOR: 0.02
};

/* =========================
   STATE
========================= */
let state = {
  xmlRemessaText: null,
  xmlVendaText: null,
  remessa: null,
  venda: null,
  depositantesSet: new Set(), // CNPJs (digits only)
  lastRules: []
};

/* =========================
   Helpers
========================= */
function onlyDigits(s){ return (s||"").toString().replace(/\D+/g,""); }

function normalizeText(s){
  if(!s) return "";
  return s.toString()
    .normalize("NFD").replace(/[\u0300-\u036f]/g,"")
    .replace(/[^\w\s]/g," ")
    .replace(/\s+/g," ")
    .trim()
    .toUpperCase();
}

function startsWithAny(text, arr){
  const t = normalizeText(text);
  return arr.some(p => t.startsWith(normalizeText(p)));
}

function getFirstText(doc, selectors){
  for(const sel of selectors){
    const el = doc.querySelector(sel);
    if(el && el.textContent != null) return el.textContent.trim();
  }
  return "";
}

function parseXml(xmlText){
  const parser = new DOMParser();
  const doc = parser.parseFromString(xmlText, "application/xml");
  const err = doc.querySelector("parsererror");
  if(err) throw new Error("XML inválido ou malformado.");
  return doc;
}

function safeNum(v){
  const n = Number(String(v||"").replace(",","."));
  return Number.isFinite(n) ? n : 0;
}

function fmtMoneyBR(n){
  const v = (Number(n)||0).toFixed(2).replace(".",",");
  return "R$ " + v.replace(/\B(?=(\d{3})+(?!\d))/g, ".");
}

function rule(status, name, detail){
  // status: OK | WARN | ERRO
  return { status, name, detail };
}

function pillClass(status){
  if(status === "OK") return "ok";
  if(status === "WARN") return "warn";
  return "err";
}

/* =========================
   Extract data from NFe XML
========================= */
function extractNFe(doc){
  // Works for both nfeProc and NFe roots
  const nfe = doc.querySelector("NFe") || doc;
  const ide = nfe.querySelector("ide");
  const dest = nfe.querySelector("dest");
  const emit = nfe.querySelector("emit");
  const total = nfe.querySelector("ICMSTot") || nfe.querySelector("total");

  // Chave (if present)
  const chave = getFirstText(doc, ["chNFe","protNFe > infProt > chNFe"]);

  // NF number
  const nNF = getFirstText(nfe, ["ide > nNF"]);

  // Natureza (natOp)
  const natOp = getFirstText(nfe, ["ide > natOp"]);

  // Dest CNPJ/CPF
  const destCnpj = getFirstText(nfe, ["dest > CNPJ"]);
  const destCpf = getFirstText(nfe, ["dest > CPF"]);
  const destDoc = destCnpj || destCpf;

  // Endereço dest
  const enderDest = nfe.querySelector("dest > enderDest");
  const cep = enderDest ? getFirstText(enderDest, ["CEP"]) : "";
  const bairro = enderDest ? getFirstText(enderDest, ["xBairro"]) : "";
  const xLgr = enderDest ? getFirstText(enderDest, ["xLgr"]) : "";
  const nro = enderDest ? getFirstText(enderDest, ["nro"]) : "";
  const xMun = enderDest ? getFirstText(enderDest, ["xMun"]) : "";
  const uf = enderDest ? getFirstText(enderDest, ["UF"]) : "";

  // Itens
  const dets = Array.from(nfe.querySelectorAll("det"));
  const itens = dets.map(det => {
    const prod = det.querySelector("prod");
    const imposto = det.querySelector("imposto");

    const cProd = prod ? getFirstText(prod, ["cProd"]) : "";
    const xProd = prod ? getFirstText(prod, ["xProd"]) : "";
    const cfop = prod ? getFirstText(prod, ["CFOP"]) : "";
    const qCom = prod ? getFirstText(prod, ["qCom"]) : "";
    const vProd = prod ? getFirstText(prod, ["vProd"]) : "";

    // ICMS: can be ICMS00/ICMS40/ICMSSN102 etc
    let cst = "";
    let csosn = "";
    if(imposto){
      const icms = imposto.querySelector("ICMS");
      if(icms){
        // find any descendant CST / CSOSN
        const cstEl = icms.querySelector("CST");
        const csosnEl = icms.querySelector("CSOSN");
        cst = cstEl ? cstEl.textContent.trim() : "";
        csosn = csosnEl ? csosnEl.textContent.trim() : "";
      }
    }

    return {
      cProd, xProd,
      CFOP: onlyDigits(cfop).slice(-4),
      qCom: safeNum(qCom),
      vProd: safeNum(vProd),
      CST: cst,
      CSOSN: csosn
    };
  });

  // Totais (prefer total tag if present)
  const vProdTotXml = getFirstText(nfe, ["total > ICMSTot > vProd", "ICMSTot > vProd"]);
  const vProdTotal = vProdTotXml ? safeNum(vProdTotXml) : itens.reduce((a,b)=>a+b.vProd,0);

  const qTotal = itens.reduce((a,b)=>a+b.qCom,0);

  // Textos adicionais p/ art129
  const infAdFisco = getFirstText(nfe, ["infAdic > infAdFisco"]);
  const infCpl = getFirstText(nfe, ["infAdic > infCpl"]);
  const textoAdic = (infAdFisco + " " + infCpl).trim();

  return {
    chave,
    nNF,
    natOp,
    destDoc,
    destCnpj: destCnpj,
    cep, bairro, xLgr, nro, xMun, uf,
    itens,
    vProdTotal,
    qTotal,
    textoAdic
  };
}

/* =========================
   Depositantes import
========================= */
function parseDepositantesText(text){
  // Accept CSV or TXT: any CNPJ in content becomes valid (digits only, 14)
  const digits = text.match(/\d{14}/g) || [];
  const set = new Set();
  for(const d of digits){
    set.add(d);
  }
  return set;
}

/* =========================
   Validation rules
========================= */
function validarTudo(){
  const rules = [];

  if(!state.remessa || !state.venda){
    rules.push(rule("ERRO","Importação XMLs","Importe XML Remessa e XML Venda antes de validar."));
    return rules;
  }

  // Update summary labels
  document.getElementById("infoChave").textContent = "Chave Remessa: " + (state.remessa.chave || "—");
  document.getElementById("infoNF").textContent = "NF Remessa: " + (state.remessa.nNF||"—") + " • NF Venda: " + (state.venda.nNF||"—");
  document.getElementById("depositanteVenda").value = formatCnpjOrDash(state.venda.destDoc);

  // 1) CNPJ Mundial x Remessa dest/CNPJ
  const remessaDestDigits = onlyDigits(state.remessa.destDoc);
  const mundialDigits = onlyDigits(CFG.CNPJ_MUNDIAL);
  if(remessaDestDigits && remessaDestDigits === mundialDigits){
    rules.push(rule("OK","CNPJ Mundial × Remessa (dest/CNPJ)","OK — destinatário é a Mundial."));
  }else{
    rules.push(rule("ERRO","CNPJ Mundial × Remessa (dest/CNPJ)",
      `Encontrado: ${formatCnpjOrDash(state.remessa.destDoc)} • Esperado: ${CFG.CNPJ_MUNDIAL}`
    ));
  }

  // 2) CEP + Bairro (Remessa enderDest)
  const cepDigits = onlyDigits(state.remessa.cep);
  const cepAceitoDigits = onlyDigits(CFG.CEP_ACEITO);
  const bairroNorm = normalizeText(state.remessa.bairro);
  const bairroOk = CFG.BAIRROS_ACEITOS.some(b => bairroNorm === normalizeText(b) || bairroNorm.includes(normalizeText(b)));
  const cepOk = cepDigits && (cepDigits === cepAceitoDigits);

  if(cepOk && bairroOk){
    rules.push(rule("OK","CEP + Bairro (Remessa enderDest)",`OK — CEP ${cepDigits} • Bairro ${bairroNorm || "—"}.`));
  }else{
    let det = [];
    det.push(`Encontrado: CEP ${cepDigits || "—"} • Bairro ${bairroNorm || "—"}`);
    det.push(`Esperado: CEP ${cepAceitoDigits} • Bairros: ${CFG.BAIRROS_ACEITOS.join(" / ")}`);
    rules.push(rule("ERRO","CEP + Bairro (Remessa enderDest)", det.join(" • ")));
  }

  // 3) Endereço (referência fixa — Base Mundial) (informativo)
  rules.push(rule("OK","Endereço (referência — Base Mundial)", CFG.ENDERECO_BASE));

  // 4) Natureza da Operação (Remessa) — prefixo REM/OUTRAS/SIMPLES
  const natRem = state.remessa.natOp || "";
  if(startsWithAny(natRem, CFG.REMESSA_PREFIXOS_OK)){
    rules.push(rule("OK","Natureza da Operação (Remessa)", `OK — "${normalizeText(natRem)}" (inicia com permitido).`));
  }else{
    rules.push(rule("ERRO","Natureza da Operação (Remessa)",
      `Encontrado: "${normalizeText(natRem)}" • Permitidos: iniciar com ${CFG.REMESSA_PREFIXOS_OK.join(" / ")}`
    ));
  }

  // 5) CST/CSOSN (Remessa) 040/041/090
  const itensRem = state.remessa.itens || [];
  const cstBad = [];
  for(const it of itensRem){
    const raw = (it.CSOSN || it.CST || "").trim();
    let norm = onlyDigits(raw);
    // CST 40 -> 040
    if(norm.length === 2) norm = "0" + norm;
    if(norm.length === 1) norm = "00" + norm;
    if(norm.length > 3) norm = norm.slice(-3);
    if(!CFG.CST_CSOSN_PERMITIDOS.includes(norm)){
      cstBad.push({cProd:it.cProd, cst: raw || "—", norm});
    }
  }
  if(cstBad.length === 0){
    rules.push(rule("OK","CST/CSOSN (Remessa) 040/041/090","OK — todos os itens com 040/041/090."));
  }else{
    const sample = cstBad.slice(0,6).map(x => `${x.cProd||"—"}:${x.norm||x.cst}`).join(" • ");
    rules.push(rule("ERRO","CST/CSOSN (Remessa) 040/041/090",
      `Itens fora do padrão: ${cstBad.length}. Ex.: ${sample}`
    ));
  }

  // 6) CFOP (Remessa)
  const cfopBad = [];
  for(const it of itensRem){
    const cf = onlyDigits(it.CFOP).slice(-4);
    if(!CFG.CFOP_PERMITIDOS.includes(cf)){
      cfopBad.push({cProd: it.cProd, cfop: it.CFOP || "—"});
    }
  }
  if(cfopBad.length === 0){
    rules.push(rule("OK","CFOP (Remessa)",`OK — todos itens em ${CFG.CFOP_PERMITIDOS.join("/")}.`));
  }else{
    const sample = cfopBad.slice(0,6).map(x => `${x.cProd||"—"}:${x.cfop}`).join(" • ");
    rules.push(rule("ERRO","CFOP (Remessa)",
      `Itens fora do permitido: ${cfopBad.length}. Ex.: ${sample} • Permitidos: ${CFG.CFOP_PERMITIDOS.join("/")}`
    ));
  }

  // 7) Art.129 (condicional)
  const precisaArt129 = itensRem.some(it => CFG.CFOP_ART129.includes(onlyDigits(it.CFOP).slice(-4)));
  if(!precisaArt129){
    rules.push(rule("OK","Art. 129 (condicional)","OK — CFOP 5.923/6.923 não presente; Art.129 não obrigatório."));
  }else{
    const hasArt = normalizeText(state.remessa.textoAdic).includes("ART 129") || normalizeText(state.remessa.textoAdic).includes("ART. 129");
    if(hasArt){
      rules.push(rule("OK","Art. 129 (condicional)","OK — CFOP exige e Art.129 encontrado no texto adicional."));
    }else{
      rules.push(rule("ERRO","Art. 129 (condicional)","CFOP 5.923/6.923 presente — exigir menção ao Art.129 (infAdFisco/infCpl)."));
    }
  }

  // 8) Natureza da Operação (Venda) — prefixo VENDA/REVENDA
  const natVenda = state.venda.natOp || "";
  if(startsWithAny(natVenda, CFG.VENDA_PREFIXOS_OK)){
    rules.push(rule("OK","Natureza da Operação (Venda)", `OK — "${normalizeText(natVenda)}" (inicia com permitido).`));
  }else{
    rules.push(rule("ERRO","Natureza da Operação (Venda)",
      `Encontrado: "${normalizeText(natVenda)}" • Permitidos: iniciar com ${CFG.VENDA_PREFIXOS_OK.join(" / ")}`
    ));
  }

  // 9) Depositante (Venda dest/CNPJ × Lista)
  const vendaDestDigits = onlyDigits(state.venda.destDoc);
  const depCount = state.depositantesSet.size;
  if(depCount === 0){
    rules.push(rule("WARN","Depositante (Venda dest/CNPJ × Lista)",
      "Lista de depositantes não carregada — importe CSV/TXT para validar."
    ));
  }else{
    if(vendaDestDigits && state.depositantesSet.has(vendaDestDigits)){
      rules.push(rule("OK","Depositante (Venda dest/CNPJ × Lista)","OK — CNPJ encontrado na lista WMS."));
    }else{
      rules.push(rule("ERRO","Depositante (Venda dest/CNPJ × Lista)",
        `CNPJ ${formatCnpjOrDash(state.venda.destDoc)} não encontrado na lista (carregados: ${depCount}).`
      ));
    }
  }

  // 10) Quantidade Remessa x Venda (total)
  const qR = Number(state.remessa.qTotal||0);
  const qV = Number(state.venda.qTotal||0);
  if(Math.abs(qR - qV) < 1e-9){
    rules.push(rule("OK","Quantidade Remessa × Venda","Compatível (totais iguais)."));
  }else{
    rules.push(rule("ERRO","Quantidade Remessa × Venda",`Divergente — Remessa: ${qR} • Venda: ${qV}`));
  }

  // 11) Valor Remessa x Venda (vProd total)
  const vR = Number(state.remessa.vProdTotal||0);
  const vV = Number(state.venda.vProdTotal||0);
  if(Math.abs(vR - vV) <= CFG.TOLERANCIA_VALOR){
    rules.push(rule("OK","Valor Remessa × Venda",`Compatível — Remessa: ${fmtMoneyBR(vR)} • Venda: ${fmtMoneyBR(vV)}`));
  }else{
    rules.push(rule("ERRO","Valor Remessa × Venda",`Divergente — Remessa: ${fmtMoneyBR(vR)} • Venda: ${fmtMoneyBR(vV)}`));
  }

  // Update natOps field
  document.getElementById("natOps").value =
    `Remessa: ${normalizeText(natRem)||"—"} | Venda: ${normalizeText(natVenda)||"—"}`;

  return rules;
}

/* =========================
   UI render + messaging
========================= */
function renderRules(rules){
  const body = document.getElementById("rulesBody");
  body.innerHTML = "";
  for(const r of rules){
    const tr = document.createElement("tr");
    tr.innerHTML = `
      <td><b>${escapeHtml(r.name)}</b></td>
      <td><span class="pill ${pillClass(r.status)}">${r.status}</span></td>
      <td>${escapeHtml(r.detail)}</td>
    `;
    body.appendChild(tr);
  }
}

function buildMensagemFornecedor(rules){
  const erros = rules.filter(r => r.status === "ERRO");
  if(erros.length === 0){
    return `✅ Documentos aprovados.\n\nAgendamento confirmado.\n`;
  }
  const linhas = erros.map(e => `❌ ${e.name} — ${e.detail}`);
  return `❌ Reprovado\n\nAjuste os pontos abaixo:\n\n${linhas.join("\n")}\n`;
}

function setResultado(aprovado){
  const el = document.getElementById("resultadoBig");
  const statusGeral = document.getElementById("statusGeral");
  if(aprovado){
    el.classList.add("ok");
    el.textContent = "✅ APROVADO";
    statusGeral.value = "Aprovado";
  }else{
    el.classList.remove("ok");
    el.textContent = "❌ REPROVADO";
    statusGeral.value = "Reprovado";
  }
}

function escapeHtml(s){
  return (s||"").toString()
    .replaceAll("&","&amp;")
    .replaceAll("<","&lt;")
    .replaceAll(">","&gt;")
    .replaceAll('"',"&quot;")
    .replaceAll("'","&#039;");
}

function formatCnpjOrDash(doc){
  const d = onlyDigits(doc);
  if(d.length === 14){
    return d.replace(/^(\d{2})(\d{3})(\d{3})(\d{4})(\d{2})$/,"$1.$2.$3/$4-$5");
  }
  if(d.length === 11){
    return d.replace(/^(\d{3})(\d{3})(\d{3})(\d{2})$/,"$1.$2.$3-$4");
  }
  return "—";
}

/* =========================
   Export CSV
========================= */
function exportCsv(){
  if(!state.lastRules || state.lastRules.length === 0){
    alert("Valide antes de exportar.");
    return;
  }
  const rows = [
    ["Regra","Status","Detalhe"],
    ...state.lastRules.map(r => [r.name, r.status, r.detail])
  ];

  const csv = rows.map(r =>
    r.map(x => `"${String(x||"").replace(/"/g,'""')}"`).join(";")
  ).join("\n");

  const blob = new Blob([csv], {type:"text/csv;charset=utf-8"});
  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");
  const nome = "relatorio_validacao_" + new Date().toISOString().slice(0,10) + ".csv";
  a.href = url;
  a.download = nome;
  document.body.appendChild(a);
  a.click();
  a.remove();
  URL.revokeObjectURL(url);
}

/* =========================
   Events
========================= */
function setFixedFields(){
  document.getElementById("cnpjMundial").value = CFG.CNPJ_MUNDIAL;
  document.getElementById("enderecoBase").value = CFG.ENDERECO_BASE;
  document.getElementById("cepAceito").value = CFG.CEP_ACEITO;
  document.getElementById("bairrosAceitos").value = CFG.BAIRROS_ACEITOS.join(" / ");
}

function limparTudo(){
  state.xmlRemessaText = null;
  state.xmlVendaText = null;
  state.remessa = null;
  state.venda = null;
  state.lastRules = [];
  document.getElementById("badgeRemessa").textContent = "não carregado";
  document.getElementById("badgeVenda").textContent = "não carregado";
  document.getElementById("nameRemessa").textContent = "—";
  document.getElementById("nameVenda").textContent = "—";
  document.getElementById("msgFornecedor").value = "";
  document.getElementById("statusGeral").value = "Aguardando validação";
  document.getElementById("depositanteVenda").value = "—";
  document.getElementById("natOps").value = "—";
  document.getElementById("infoChave").textContent = "Chave Remessa: —";
  document.getElementById("infoNF").textContent = "NF Remessa: — • NF Venda: —";
  renderRules([]);
  setResultado(false);
}

document.addEventListener("DOMContentLoaded", () => {
  setFixedFields();
  renderRules([]);
  setResultado(false);

  // Buttons open hidden inputs
  document.getElementById("btnPickRemessa").addEventListener("click", () => document.getElementById("fileRemessa").click());
  document.getElementById("btnPickVenda").addEventListener("click", () => document.getElementById("fileVenda").click());
  document.getElementById("btnPickDepositantes").addEventListener("click", () => document.getElementById("fileDepositantes").click());

  // File change handlers
  document.getElementById("fileRemessa").addEventListener("change", async (e) => {
    const f = e.target.files && e.target.files[0];
    if(!f) return;
    try{
      const text = await f.text();
      const doc = parseXml(text);
      state.xmlRemessaText = text;
      state.remessa = extractNFe(doc);

      document.getElementById("badgeRemessa").textContent = "carregado";
      document.getElementById("nameRemessa").textContent = f.name;
    }catch(err){
      alert("Falha ao ler XML Remessa: " + (err.message || err));
      state.remessa = null;
      document.getElementById("badgeRemessa").textContent = "erro";
      document.getElementById("nameRemessa").textContent = "—";
    }
  });

  document.getElementById("fileVenda").addEventListener("change", async (e) => {
    const f = e.target.files && e.target.files[0];
    if(!f) return;
    try{
      const text = await f.text();
      const doc = parseXml(text);
      state.xmlVendaText = text;
      state.venda = extractNFe(doc);

      document.getElementById("badgeVenda").textContent = "carregado";
      document.getElementById("nameVenda").textContent = f.name;
    }catch(err){
      alert("Falha ao ler XML Venda: " + (err.message || err));
      state.venda = null;
      document.getElementById("badgeVenda").textContent = "erro";
      document.getElementById("nameVenda").textContent = "—";
    }
  });

  document.getElementById("fileDepositantes").addEventListener("change", async (e) => {
    const f = e.target.files && e.target.files[0];
    if(!f) return;
    try{
      const text = await f.text();
      state.depositantesSet = parseDepositantesText(text);
      document.getElementById("infoDepositantes").textContent = "Depositantes carregados: " + state.depositantesSet.size;
      alert("Depositantes importados: " + state.depositantesSet.size);
    }catch(err){
      alert("Falha ao importar depositantes: " + (err.message || err));
    }
  });

  // Validate
  document.getElementById("btnValidar").addEventListener("click", () => {
    const rules = validarTudo();
    state.lastRules = rules;
    renderRules(rules);

    const aprovado = rules.every(r => r.status !== "ERRO");
    setResultado(aprovado);

    const msg = buildMensagemFornecedor(rules);
    document.getElementById("msgFornecedor").value = msg;
  });

  // Export
  document.getElementById("btnExport").addEventListener("click", exportCsv);

  // Clear
  document.getElementById("btnLimpar").addEventListener("click", () => {
    if(confirm("Limpar tudo?")){
      limparTudo();
      // não limpa depositantes (mantém, como calculadora)
      document.getElementById("infoDepositantes").textContent = "Depositantes carregados: " + state.depositantesSet.size;
      setFixedFields();
    }
  });

  // initial
  document.getElementById("infoDepositantes").textContent = "Depositantes carregados: " + state.depositantesSet.size;
});
</script>
</body>
</html>
