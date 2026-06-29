---
title: "Configuratore Token HyperRetailCloud"
date: "2026-06-26"
categoria: software HyperRetailCloud
creato da: Robuschi Ivan
Azienda: Custom S.p.A.
Software: HyperRetailCloud
Categoria: software Cloud
Revision: 1
Settori commerciali: horeca, tabacchi, retail, stagionali
Destinatario del documento: partners, dealer, supporto, sales
summary: "Configuratore interattivo per il calcolo dei token e dei costi mensili di HyperRetailCloud. Seleziona i moduli e i mesi di utilizzo per ottenere una stima immediata del canone e dei token necessari."
capitolo: 9
fonte: HyperCloud_04_IPiani.docx
Keywords:
  - configuratore
  - token
  - calcolo-costi
  - moduli
  - canone-mensile
  - preventivo
---

# 🧮 Configuratore Token HyperRetailCloud

**HyperRetailCloud — Formazione Commerciale** | *Custom S.p.A. © 2026*

Seleziona i moduli, i mesi di utilizzo e ottieni subito il calcolo dei token e del costo. Usalo durante la visita commerciale per costruire un preventivo sul momento.

<div id="configuratore-hrc">
<style>
  #configuratore-hrc {
    font-family: var(--md-text-font, 'Titillium Web', sans-serif);
    margin: 1.5rem 0;
  }
  .cfg-card {
    background: var(--md-code-bg-color, #f5f5f5);
    border: 1px solid var(--md-default-fg-color--lightest, #ddd);
    border-radius: 8px;
    padding: 1.2rem 1.5rem;
    margin-bottom: 1.2rem;
  }
  .cfg-card h3 {
    margin: 0 0 1rem 0;
    font-size: 1rem;
    font-weight: 700;
    color: var(--md-primary-fg-color, #89A9C2);
    border-bottom: 2px solid var(--md-primary-fg-color, #89A9C2);
    padding-bottom: 0.4rem;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }
  .profili-grid {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }
  .profilo-btn {
    background: var(--md-default-bg-color, #fff);
    border: 2px solid var(--md-primary-fg-color, #89A9C2);
    color: var(--md-primary-fg-color, #89A9C2);
    border-radius: 20px;
    padding: 0.35rem 1rem;
    font-size: 0.85rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.15s ease;
  }
  .profilo-btn:hover, .profilo-btn.active {
    background: var(--md-primary-fg-color, #89A9C2);
    color: #fff;
  }
  .modulo-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.5rem 0;
    border-bottom: 1px solid var(--md-default-fg-color--lightest, #eee);
    gap: 1rem;
  }
  .modulo-row:last-child { border-bottom: none; }
  .modulo-left {
    display: flex;
    align-items: center;
    gap: 0.7rem;
    flex: 1;
  }
  .modulo-left input[type="checkbox"] {
    width: 18px;
    height: 18px;
    accent-color: var(--md-primary-fg-color, #89A9C2);
    cursor: pointer;
    flex-shrink: 0;
  }
  .modulo-info { flex: 1; }
  .modulo-nome {
    font-weight: 600;
    font-size: 0.9rem;
    color: var(--md-default-fg-color, #333);
  }
  .modulo-nome.base { color: var(--md-primary-fg-color, #89A9C2); }
  .modulo-desc {
    font-size: 0.78rem;
    color: var(--md-default-fg-color--light, #666);
    margin-top: 0.1rem;
  }
  .modulo-costo {
    font-size: 0.85rem;
    font-weight: 700;
    color: var(--md-primary-fg-color, #89A9C2);
    white-space: nowrap;
    min-width: 90px;
    text-align: right;
  }
  .modulo-costo.base { color: var(--md-default-fg-color--light, #888); }
  .modulo-row.disabled { opacity: 0.45; }
  .cfg-row-2col {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 1.2rem;
  }
  @media (max-width: 600px) { .cfg-row-2col { grid-template-columns: 1fr; } }
  .cfg-label {
    font-size: 0.85rem;
    font-weight: 600;
    color: var(--md-default-fg-color, #333);
    margin-bottom: 0.5rem;
    display: block;
  }
  .cfg-slider-wrap {
    display: flex;
    align-items: center;
    gap: 0.8rem;
  }
  .cfg-slider {
    flex: 1;
    accent-color: var(--md-primary-fg-color, #89A9C2);
    height: 6px;
    cursor: pointer;
  }
  .cfg-slider-val {
    font-size: 1.2rem;
    font-weight: 800;
    color: var(--md-primary-fg-color, #89A9C2);
    min-width: 2.5rem;
    text-align: center;
  }
  .cfg-input {
    width: 100%;
    padding: 0.4rem 0.7rem;
    border: 2px solid var(--md-default-fg-color--lightest, #ddd);
    border-radius: 6px;
    font-size: 1rem;
    font-weight: 700;
    color: var(--md-default-fg-color, #333);
    background: var(--md-default-bg-color, #fff);
    box-sizing: border-box;
  }
  .cfg-input:focus {
    outline: none;
    border-color: var(--md-primary-fg-color, #89A9C2);
  }
  .risultati-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(160px, 1fr));
    gap: 1rem;
    margin-bottom: 1rem;
  }
  .ris-box {
    background: var(--md-default-bg-color, #fff);
    border: 2px solid var(--md-primary-fg-color, #89A9C2);
    border-radius: 8px;
    padding: 0.8rem 1rem;
    text-align: center;
  }
  .ris-box.highlight {
    background: var(--md-primary-fg-color, #89A9C2);
    color: #fff;
  }
  .ris-label {
    font-size: 0.72rem;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    font-weight: 600;
    opacity: 0.75;
    margin-bottom: 0.3rem;
  }
  .ris-val {
    font-size: 1.6rem;
    font-weight: 900;
    line-height: 1.1;
  }
  .ris-unit {
    font-size: 0.78rem;
    font-weight: 600;
    opacity: 0.8;
  }
  .riepilogo-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 0.88rem;
    margin-top: 0.5rem;
  }
  .riepilogo-table td {
    padding: 0.35rem 0.5rem;
    border-bottom: 1px solid var(--md-default-fg-color--lightest, #eee);
    color: var(--md-default-fg-color, #333);
  }
  .riepilogo-table td:last-child {
    text-align: right;
    font-weight: 700;
  }
  .riepilogo-table tr.totale td {
    border-top: 2px solid var(--md-primary-fg-color, #89A9C2);
    border-bottom: none;
    font-weight: 800;
    font-size: 1rem;
    color: var(--md-primary-fg-color, #89A9C2);
  }
  .cfg-note {
    font-size: 0.78rem;
    color: var(--md-default-fg-color--light, #888);
    margin-top: 0.8rem;
    font-style: italic;
  }
</style>

<!-- PROFILI RAPIDI -->
<div class="cfg-card">
  <h3>⚡ Profili rapidi</h3>
  <div class="profili-grid">
    <button class="profilo-btn" onclick="applicaProfilo('bar')">☕ Bar</button>
    <button class="profilo-btn" onclick="applicaProfilo('tabacchi')">🚬 Tabacchi Easy</button>
    <button class="profilo-btn" onclick="applicaProfilo('tabacchi_adv')">🚬 Tabacchi + BackOffice</button>
    <button class="profilo-btn" onclick="applicaProfilo('ristorante')">🍽️ Ristorante</button>
    <button class="profilo-btn" onclick="applicaProfilo('general')">🛒 General Store</button>
    <button class="profilo-btn" onclick="applicaProfilo('minimarket')">🏪 MiniMarket + Bilance</button>
    <button class="profilo-btn" onclick="applicaProfilo('stagionale')">🌊 Stagionale</button>
    <button class="profilo-btn" onclick="applicaProfilo('full')">🔝 Configurazione completa</button>
  </div>
</div>

<!-- MODULI -->
<div class="cfg-card">
  <h3>🧩 Seleziona i moduli</h3>

  <div class="modulo-row">
    <div class="modulo-left">
      <input type="checkbox" id="mod_base" checked disabled>
      <div class="modulo-info">
        <div class="modulo-nome base">HyperRetailCloud — Licenza Base</div>
        <div class="modulo-desc">Cassa, anagrafica cloud, offline-first, conti sospesi — incluso sempre</div>
      </div>
    </div>
    <div class="modulo-costo base">0,4 tok/mese</div>
  </div>

  <div class="modulo-row">
    <div class="modulo-left">
      <input type="checkbox" id="mod_ristorazione" onchange="aggiorna()">
      <div class="modulo-info">
        <div class="modulo-nome">Modulo Ristorazione</div>
        <div class="modulo-desc">Gestione tavoli, comande, stampa cucina, asporto</div>
      </div>
    </div>
    <div class="modulo-costo">+0,1 tok/mese</div>
  </div>

  <div class="modulo-row">
    <div class="modulo-left">
      <input type="checkbox" id="mod_monopolio" onchange="aggiorna()">
      <div class="modulo-info">
        <div class="modulo-nome">Modulo Monopolio — Tabacchi</div>
        <div class="modulo-desc">Anagrafica tabacchi aggiornata in real-time, gestione stecche, riordino AI</div>
      </div>
    </div>
    <div class="modulo-costo">+0,1 tok/mese</div>
  </div>

  <div class="modulo-row">
    <div class="modulo-left">
      <input type="checkbox" id="mod_hyperstore" onchange="onHyperstoreChange()">
      <div class="modulo-info">
        <div class="modulo-nome">HyperStore — BackOffice</div>
        <div class="modulo-desc">Statistiche AI, magazzino base, gestione clienti (richiede PC Windows)</div>
      </div>
    </div>
    <div class="modulo-costo">+0,1 tok/mese</div>
  </div>

  <div class="modulo-row" id="row_plus">
    <div class="modulo-left">
      <input type="checkbox" id="mod_plus" onchange="aggiorna()" disabled>
      <div class="modulo-info">
        <div class="modulo-nome">Modulo PLUS — Magazzino avanzato</div>
        <div class="modulo-desc">Carico/scarico, inventario, ordini fornitori — richiede HyperStore attivo</div>
      </div>
    </div>
    <div class="modulo-costo">+0,1 tok/mese</div>
  </div>

  <div class="modulo-row">
    <div class="modulo-left">
      <input type="checkbox" id="mod_liveretail" onchange="aggiorna()">
      <div class="modulo-info">
        <div class="modulo-nome">LiveRetail — Integrazione Bilance</div>
        <div class="modulo-desc">Sincronizzazione anagrafica bilance Custom/Macchi Icona, lettura QR Code</div>
      </div>
    </div>
    <div class="modulo-costo">+0,1 tok/mese</div>
  </div>
</div>

<!-- PARAMETRI -->
<div class="cfg-card">
  <h3>⚙️ Parametri</h3>
  <div class="cfg-row-2col">
    <div>
      <span class="cfg-label">📅 Mesi di utilizzo all'anno</span>
      <div class="cfg-slider-wrap">
        <input type="range" class="cfg-slider" id="slider_mesi" min="1" max="12" value="12" oninput="aggiornaMesi(this.value)">
        <div class="cfg-slider-val" id="val_mesi">12</div>
      </div>
      <div style="display:flex;justify-content:space-between;font-size:0.72rem;color:#999;margin-top:0.2rem;">
        <span>1 mese</span><span>6 mesi</span><span>12 mesi</span>
      </div>
    </div>
    <div>
      <span class="cfg-label">💶 Prezzo unitario del token (€)</span>
      <input type="number" class="cfg-input" id="input_prezzo" value="50" min="1" step="1" oninput="aggiorna()">
      <div style="font-size:0.75rem;color:#999;margin-top:0.3rem;">Standard € 50 — verifica promozioni con il tuo Area Manager</div>
    </div>
  </div>
</div>

<!-- RISULTATI -->
<div class="cfg-card">
  <h3>📊 Risultati</h3>
  <div class="risultati-grid">
    <div class="ris-box">
      <div class="ris-label">Attivazione (una tantum)</div>
      <div class="ris-val">1</div>
      <div class="ris-unit">token</div>
    </div>
    <div class="ris-box">
      <div class="ris-label">Token / mese</div>
      <div class="ris-val" id="out_tok_mese">0,4</div>
      <div class="ris-unit">token/mese</div>
    </div>
    <div class="ris-box">
      <div class="ris-label">Token totali (<span id="out_mesi_label">12</span> mesi + att.)</div>
      <div class="ris-val" id="out_tok_tot">5,8</div>
      <div class="ris-unit">token</div>
    </div>
    <div class="ris-box highlight">
      <div class="ris-label">Costo totale stimato</div>
      <div class="ris-val" id="out_costo_tot">€ 290</div>
      <div class="ris-unit" id="out_costo_detail">€ 50 att. + € 240 canone</div>
    </div>
  </div>

  <table class="riepilogo-table">
    <tbody id="riepilogo_body">
    </tbody>
    <tr class="totale">
      <td>TOTALE stimato</td>
      <td id="out_totale_riga">€ 290,00</td>
    </tr>
  </table>

  <p class="cfg-note">* I prezzi sono indicativi al costo standard di € 50/token. Promozioni volume possono ridurre il costo unitario. Contatta il tuo Area Manager per le condizioni riservate ai partner.</p>
</div>

<script>
function aggiornaMesi(val) {
  document.getElementById('val_mesi').textContent = val;
  aggiorna();
}

function onHyperstoreChange() {
  const hs = document.getElementById('mod_hyperstore').checked;
  const plusCb = document.getElementById('mod_plus');
  const plusRow = document.getElementById('row_plus');
  if (!hs) {
    plusCb.checked = false;
    plusCb.disabled = true;
    plusRow.classList.add('disabled');
  } else {
    plusCb.disabled = false;
    plusRow.classList.remove('disabled');
  }
  aggiorna();
}

function aggiorna() {
  const prezzoToken = parseFloat(document.getElementById('input_prezzo').value) || 50;
  const mesi = parseInt(document.getElementById('slider_mesi').value);

  let tokMese = 0.4;
  const moduli = [];
  moduli.push({ nome: 'HyperRetailCloud — Licenza Base', tok: 0.4 });

  if (document.getElementById('mod_ristorazione').checked) {
    tokMese += 0.1;
    moduli.push({ nome: 'Modulo Ristorazione', tok: 0.1 });
  }
  if (document.getElementById('mod_monopolio').checked) {
    tokMese += 0.1;
    moduli.push({ nome: 'Modulo Monopolio — Tabacchi', tok: 0.1 });
  }
  if (document.getElementById('mod_hyperstore').checked) {
    tokMese += 0.1;
    moduli.push({ nome: 'HyperStore — BackOffice', tok: 0.1 });
  }
  if (document.getElementById('mod_plus').checked) {
    tokMese += 0.1;
    moduli.push({ nome: 'Modulo PLUS — Magazzino avanzato', tok: 0.1 });
  }
  if (document.getElementById('mod_liveretail').checked) {
    tokMese += 0.1;
    moduli.push({ nome: 'LiveRetail — Bilance', tok: 0.1 });
  }

  const tokTot = 1 + (tokMese * mesi);
  const costoAtt = prezzoToken;
  const costoCanone = tokMese * mesi * prezzoToken;
  const costoTot = costoAtt + costoCanone;

  // Aggiorna valori
  document.getElementById('out_tok_mese').textContent = tokMese.toFixed(1).replace('.', ',');
  document.getElementById('out_tok_tot').textContent = tokTot.toFixed(1).replace('.', ',');
  document.getElementById('out_mesi_label').textContent = mesi;
  document.getElementById('out_costo_tot').textContent = '€ ' + Math.round(costoTot).toLocaleString('it-IT');
  document.getElementById('out_costo_detail').textContent = '€ ' + Math.round(costoAtt) + ' att. + € ' + Math.round(costoCanone) + ' canone';
  document.getElementById('out_totale_riga').textContent = '€ ' + costoTot.toFixed(2).replace('.', ',');

  // Riepilogo tabella
  let html = '';
  html += '<tr><td>Attivazione licenza (una tantum)</td><td>1 token = € ' + costoAtt.toFixed(2).replace('.', ',') + '</td></tr>';
  moduli.forEach(m => {
    const euroMese = (m.tok * prezzoToken).toFixed(2).replace('.', ',');
    const euroTot = (m.tok * mesi * prezzoToken).toFixed(2).replace('.', ',');
    html += '<tr><td>' + m.nome + ' × ' + mesi + ' mesi</td><td>' + m.tok.toFixed(1).replace('.', ',') + ' tok × ' + mesi + ' = ' + (m.tok * mesi).toFixed(1).replace('.', ',') + ' tok → € ' + euroTot + '</td></tr>';
  });
  document.getElementById('riepilogo_body').innerHTML = html;
}

function applicaProfilo(profilo) {
  // Reset tutti i moduli
  ['mod_ristorazione','mod_monopolio','mod_hyperstore','mod_plus','mod_liveretail'].forEach(id => {
    document.getElementById(id).checked = false;
  });
  document.getElementById('mod_plus').disabled = true;
  document.getElementById('row_plus').classList.add('disabled');

  // Reset profili attivi
  document.querySelectorAll('.profilo-btn').forEach(b => b.classList.remove('active'));
  event.target.classList.add('active');

  switch(profilo) {
    case 'bar':
      document.getElementById('mod_ristorazione').checked = true;
      document.getElementById('slider_mesi').value = 12;
      document.getElementById('val_mesi').textContent = 12;
      break;
    case 'tabacchi':
      document.getElementById('mod_monopolio').checked = true;
      document.getElementById('slider_mesi').value = 12;
      document.getElementById('val_mesi').textContent = 12;
      break;
    case 'tabacchi_adv':
      document.getElementById('mod_monopolio').checked = true;
      document.getElementById('mod_hyperstore').checked = true;
      document.getElementById('mod_plus').disabled = false;
      document.getElementById('row_plus').classList.remove('disabled');
      document.getElementById('slider_mesi').value = 12;
      document.getElementById('val_mesi').textContent = 12;
      break;
    case 'ristorante':
      document.getElementById('mod_ristorazione').checked = true;
      document.getElementById('mod_hyperstore').checked = true;
      document.getElementById('mod_plus').disabled = false;
      document.getElementById('row_plus').classList.remove('disabled');
      document.getElementById('slider_mesi').value = 12;
      document.getElementById('val_mesi').textContent = 12;
      break;
    case 'general':
      document.getElementById('slider_mesi').value = 12;
      document.getElementById('val_mesi').textContent = 12;
      break;
    case 'minimarket':
      document.getElementById('mod_hyperstore').checked = true;
      document.getElementById('mod_plus').disabled = false;
      document.getElementById('row_plus').classList.remove('disabled');
      document.getElementById('mod_liveretail').checked = true;
      document.getElementById('slider_mesi').value = 12;
      document.getElementById('val_mesi').textContent = 12;
      break;
    case 'stagionale':
      document.getElementById('mod_ristorazione').checked = true;
      document.getElementById('slider_mesi').value = 5;
      document.getElementById('val_mesi').textContent = 5;
      break;
    case 'full':
      ['mod_ristorazione','mod_monopolio','mod_hyperstore','mod_liveretail'].forEach(id => {
        document.getElementById(id).checked = true;
      });
      document.getElementById('mod_plus').disabled = false;
      document.getElementById('mod_plus').checked = true;
      document.getElementById('row_plus').classList.remove('disabled');
      document.getElementById('slider_mesi').value = 12;
      document.getElementById('val_mesi').textContent = 12;
      break;
  }
  aggiorna();
}

// Init
aggiorna();
</script>
</div>

---

[← I Piani e i Token](i_piani.md) | [HyperRetailCloud e l'AI →](ai.md)

*Custom S.p.A. © 2026 — Uso riservato ai concessionari autorizzati*
