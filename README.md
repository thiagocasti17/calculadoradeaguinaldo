[index.html](https://github.com/user-attachments/files/33686638/index.html)
# calculadoradeaguinaldo
Calculadora de aguinaldo (SAC) para Argentina. Calculá el bruto, el neto estimado y el proporcional si no trabajaste todo el semestre, con descuentos del 17% (jubilación, obra social y PAMI). Gratis, sin registro y sin dependencias: HTML, CSS y JavaScript puro, listo para publicar en Netlify. Resultados orientativos, no reemplaza a un contador.
<!DOCTYPE html>
<html lang="es-AR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Calculadora de aguinaldo 2026 (SAC) en Argentina</title>
<meta name="description" content="Calculá tu aguinaldo (sueldo anual complementario) en segundos: bruto, neto y proporcional si no trabajaste todo el semestre. Actualizado a 2026.">
<!-- Reemplazá TU-SITIO por tu dominio real -->
<link rel="canonical" href="https://TU-SITIO.netlify.app/">
<meta property="og:title" content="Calculadora de aguinaldo 2026 (SAC) en Argentina">
<meta property="og:description" content="Aguinaldo bruto, neto y proporcional. Gratis y sin registro.">
<meta property="og:type" content="website">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Schibsted+Grotesk:wght@400;600;800&family=Source+Serif+4:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
<script type="application/ld+json">
{"@context":"https://schema.org","@type":"FAQPage","mainEntity":[
{"@type":"Question","name":"¿Cuándo se cobra el aguinaldo?","acceptedAnswer":{"@type":"Answer","text":"En dos cuotas: hasta el 30 de junio y hasta el 18 de diciembre. La ley admite hasta cuatro días hábiles más de plazo."}},
{"@type":"Question","name":"¿La reforma laboral cambió el cálculo del aguinaldo?","acceptedAnswer":{"@type":"Answer","text":"No. Sigue siendo el 50% de la mayor remuneración mensual del semestre. Lo que cambió es la clasificación de algunos conceptos, como los beneficios sociales, así que conviene revisar qué incluye tu mejor sueldo."}},
{"@type":"Question","name":"¿El aguinaldo paga Ganancias?","acceptedAnswer":{"@type":"Answer","text":"Si tu sueldo está alcanzado por Ganancias de cuarta categoría, el aguinaldo se suma a la base y puede aumentar la retención. Esta calculadora no incluye ese impuesto."}},
{"@type":"Question","name":"¿Qué pasa con el aguinaldo si renuncio o me despiden?","acceptedAnswer":{"@type":"Answer","text":"Cobrás la parte proporcional a los días trabajados del semestre, junto con la liquidación final."}}
]}
</script>
<style>
:root{--fondo:#EAF1F5;--papel:#fff;--tinta:#18222D;--tinta2:#4A5866;--celeste:#1B6CA8;--sol:#F6B93B;--linea:#CBD7E0}
*{box-sizing:border-box}
body{margin:0;background:var(--fondo);color:var(--tinta);font:17px/1.7 "Source Serif 4",Georgia,serif}
h1,h2,label,button,.ui,summary{font-family:"Schibsted Grotesk",system-ui,sans-serif}
.wrap{max-width:1040px;margin:0 auto;padding:0 20px}
header{padding:28px 0 8px}
.marca{font:600 .95rem "Schibsted Grotesk",system-ui,sans-serif;color:var(--celeste)}
h1{font-size:clamp(2rem,6vw,3.5rem);line-height:1.05;letter-spacing:-.02em;font-weight:800;margin:14px 0 10px;max-width:16ch}
.sub{margin:0 0 28px;color:var(--tinta2);max-width:56ch}
.calc{display:grid;gap:24px;grid-template-columns:minmax(0,1fr) minmax(0,1.1fr);align-items:start}
@media(max-width:820px){.calc{grid-template-columns:minmax(0,1fr)}}
.form{background:var(--papel);border:1px solid var(--linea);border-radius:14px;padding:24px}
.campo{margin-bottom:18px}
label{display:block;font-weight:600;font-size:.98rem;margin-bottom:6px}
.ayuda{display:block;font:400 .88rem/1.4 "Source Serif 4",Georgia,serif;color:var(--tinta2);margin-top:5px}
input,select{width:100%;font:inherit;font-size:1rem;font-family:"Schibsted Grotesk",system-ui,sans-serif;padding:12px;border:1.5px solid #9FB3C3;border-radius:8px;background:#fff;color:var(--tinta)}
input:focus-visible,select:focus-visible,summary:focus-visible,.chk input:focus-visible{outline:3px solid var(--celeste);outline-offset:2px}
.dos{display:grid;grid-template-columns:1fr 1fr;gap:12px}
.chk{display:flex;gap:10px;align-items:center;font-weight:400;cursor:pointer}
.chk input{width:20px;height:20px;margin:0;accent-color:var(--celeste)}
#fechas{display:none;margin-top:14px}
#fechas.on{display:block}
.recibo{position:relative;background:var(--papel);padding:24px 24px 28px;border-radius:4px 4px 0 0;margin-bottom:18px;box-shadow:0 1px 0 var(--linea)}
.recibo::after{content:"";position:absolute;left:0;right:0;bottom:-14px;height:14px;background:linear-gradient(135deg,var(--papel) 25%,transparent 25%) 0 0/14px 14px,linear-gradient(225deg,var(--papel) 25%,transparent 25%) 0 0/14px 14px}
.recibo h2{font-size:1.1rem;margin:0 0 12px;font-weight:800}
.fila{display:grid;grid-template-columns:minmax(0,1fr) 7.2rem 6.2rem;gap:4px 12px;padding:8px 0;border-bottom:1px dashed var(--linea);font:400 .93rem/1.35 "Schibsted Grotesk",system-ui,sans-serif}
.fila.cab{color:var(--tinta2);font-size:.82rem;border-bottom:1.5px solid var(--tinta)}
.fila span:nth-child(n+2){text-align:right;font-variant-numeric:tabular-nums}
.fila.paso{color:var(--tinta2)}
.fila.fuerte{font-weight:600}
.neto{display:flex;justify-content:space-between;align-items:baseline;gap:12px;flex-wrap:wrap;background:var(--sol);border-radius:6px;padding:14px 16px;margin-top:16px;font-family:"Schibsted Grotesk",system-ui,sans-serif}
.neto b{font-size:clamp(1.5rem,5vw,2rem);font-weight:800;font-variant-numeric:tabular-nums}
.nota{font-size:.9rem;color:var(--tinta2);margin:14px 0 0}
.err{color:#A12B2B;font:600 .92rem "Schibsted Grotesk",system-ui,sans-serif;margin:8px 0 0}
.donar{margin-top:28px;background:var(--papel);border:1px solid var(--linea);border-radius:14px;padding:24px;text-align:center}
.donar[hidden]{display:none}
.donar h2{font-size:1.35rem;margin:0 0 6px;font-weight:800;letter-spacing:-.01em}
.donar p{margin:0 auto 18px;max-width:52ch;color:var(--tinta2)}
.montos{display:grid;grid-template-columns:repeat(3,minmax(0,1fr));gap:12px}
@media(max-width:620px){.montos{grid-template-columns:minmax(0,1fr)}}
.monto{position:relative;display:block;text-decoration:none;color:var(--tinta);background:#fff;border:1.5px solid #9FB3C3;border-radius:10px;padding:14px 10px;font-family:"Schibsted Grotesk",system-ui,sans-serif}
.monto b{display:block;font-size:1.05rem}
.monto span{font-size:.9rem;color:var(--tinta2)}
.monto:hover{border-color:var(--celeste)}
.monto:focus-visible{outline:3px solid var(--celeste);outline-offset:2px}
.monto.top{background:var(--sol);border-color:var(--sol)}
.monto.top span{color:var(--tinta)}
.monto i{position:absolute;top:-10px;left:50%;transform:translateX(-50%);background:var(--tinta);color:#fff;font:600 .75rem "Schibsted Grotesk",system-ui,sans-serif;font-style:normal;padding:2px 10px;border-radius:99px;white-space:nowrap}
.donar small{display:block;margin-top:16px;color:var(--tinta2);font:400 .85rem "Schibsted Grotesk",system-ui,sans-serif}
.anuncio{margin:36px 0;min-height:90px}
article{max-width:68ch;padding:8px 0 24px}
article h2{font-size:1.5rem;letter-spacing:-.01em;margin:36px 0 8px}
details{border-top:1px solid var(--linea);padding:12px 0}
summary{font-weight:600;cursor:pointer}
details p{margin:8px 0 0}
footer{border-top:1px solid var(--linea);padding:20px 0 40px;color:var(--tinta2);font-size:.9rem}
@media(prefers-reduced-motion:reduce){*{scroll-behavior:auto!important}}
</style>
</head>
<body>
<div class="wrap">
<header>
  <div class="marca">Calculadoras argentinas</div>
  <h1>Calculadora de aguinaldo 2026</h1>
  <p class="sub">Ingresá tu mejor sueldo del semestre y mirá cuánto te toca de aguinaldo, en bruto y en neto. Si entraste o te fuiste a mitad del semestre, también lo calcula proporcional.</p>
</header>

<main>
<section class="calc" aria-label="Calculadora">
  <div class="form">
    <div class="dos campo">
      <div>
        <label for="sem">Semestre</label>
        <select id="sem"><option value="1">1.º (enero a junio)</option><option value="2">2.º (julio a diciembre)</option></select>
      </div>
      <div>
        <label for="anio">Año</label>
        <input id="anio" type="number" inputmode="numeric" min="2020" max="2100">
      </div>
    </div>
    <div class="campo">
      <label for="sueldo">Mejor sueldo bruto del semestre ($)</label>
      <input id="sueldo" type="text" inputmode="decimal" placeholder="Ej: 1.200.000" autocomplete="off">
      <span class="ayuda">Tomá el mes en que más cobraste, con horas extras, comisiones y adicionales.</span>
    </div>
    <div class="campo">
      <label class="chk"><input type="checkbox" id="parcial"> Entré o me fui durante el semestre</label>
      <div id="fechas">
        <div class="dos">
          <div><label for="desde">Desde</label><input id="desde" type="date"></div>
          <div><label for="hasta">Hasta</label><input id="hasta" type="date"></div>
        </div>
        <p class="err" id="err" role="alert" hidden></p>
      </div>
    </div>
  </div>

  <div>
    <div class="recibo" aria-live="polite">
      <h2>Tu liquidación</h2>
      <div class="fila cab"><span>Concepto</span><span>Remuneraciones</span><span>Descuentos</span></div>
      <div class="fila paso"><span>Mejor sueldo del semestre</span><span id="r1">—</span><span></span></div>
      <div class="fila paso"><span>Mitad (50%)</span><span id="r2">—</span><span></span></div>
      <div class="fila paso"><span id="rdias">Días trabajados</span><span id="r3">—</span><span></span></div>
      <div class="fila fuerte"><span>Aguinaldo bruto</span><span id="r4">—</span><span></span></div>
      <div class="fila"><span>Jubilación (11%)</span><span></span><span id="d1">—</span></div>
      <div class="fila"><span>Obra social (3%)</span><span></span><span id="d2">—</span></div>
      <div class="fila"><span>Ley 19.032, PAMI (3%)</span><span></span><span id="d3">—</span></div>
      <div class="fila fuerte"><span>Total descuentos</span><span></span><span id="d4">—</span></div>
      <div class="neto"><span>Neto estimado a cobrar</span><b id="neto">—</b></div>
      <p class="nota" id="pago"></p>
    </div>
  </div>
</section>

<!-- Donaciones: pegá tus links de pago de Mercado Pago en los 3 href (el bloque se muestra solo cuando los reemplazás) -->
<section class="donar" id="donar" hidden aria-labelledby="donar-t">
  <h2 id="donar-t">Este cálculo es gratis. ¿Nos invitás un café?</h2>
  <p>Mantener las calculadoras al día lleva muchas horas por mes. Con tu aporte seguimos siendo gratis y sin paywall.</p>
  <div class="montos">
    <a class="monto" href="https://mpago.li/13ZnUsm" target="_blank" rel="noopener">☕ <b>Un café</b><span>$3.000</span></a>
    <a class="monto top" href="https://mpago.li/1pMdWqL" target="_blank" rel="noopener"><i>Más elegido</i>🍕 <b>Una pizza</b><span>$7.000</span></a>
    <a class="monto" href="https://mpago.li/1kNpAxM" target="_blank" rel="noopener">💪 <b>Bancanos un mes</b><span>$15.000</span></a>
  </div>
  <small>Pagás con tarjeta, transferencia o dinero en cuenta de Mercado Pago.</small>
</section>

<!-- Espacio para anuncio (AdSense) -->
<div class="anuncio" aria-hidden="true"></div>

<article>
  <h2>Cómo se calcula el aguinaldo</h2>
  <p>El aguinaldo, o sueldo anual complementario (SAC), se paga dos veces por año y equivale al 50% de la mayor remuneración mensual que cobraste en cada semestre. La cuenta es simple: tomás tu mejor sueldo del período, lo dividís por dos y ese es tu aguinaldo bruto.</p>
  <p>Cuenta todo lo que sea remunerativo: sueldo básico, horas extras, comisiones, adicionales y premios habituales. Por eso el mejor mes no siempre es el de sueldo básico más alto.</p>

  <h2>Ejemplo con un semestre completo</h2>
  <p>Si tu mejor sueldo del segundo semestre fue de $1.200.000, el aguinaldo bruto es $600.000. Con los descuentos habituales del 17% (jubilación, obra social y PAMI), te quedan unos $498.000 netos.</p>

  <h2>Si no trabajaste todo el semestre</h2>
  <p>Cuando entrás a trabajar después del 1.º de enero o del 1.º de julio, o dejás el empleo antes de que termine el semestre, cobrás la parte proporcional a los días trabajados. Siguiendo el ejemplo anterior, si empezaste el 1.º de septiembre trabajaste 122 de los 184 días del semestre: $600.000 × 122 ÷ 184 = $397.826 brutos.</p>

  <h2>Descuentos del aguinaldo</h2>
  <p>Al aguinaldo se le aplican los mismos aportes que al sueldo: 11% de jubilación, 3% de obra social y 3% de la Ley 19.032 (PAMI). Según tu convenio puede haber otros, como la cuota sindical. Si tu sueldo paga Ganancias, el aguinaldo también puede aumentar la retención de ese mes.</p>

  <h2>Preguntas frecuentes</h2>
  <details><summary>¿Cuándo se cobra el aguinaldo?</summary><p>En dos cuotas: hasta el 30 de junio y hasta el 18 de diciembre. La ley admite hasta cuatro días hábiles más de plazo.</p></details>
  <details><summary>¿La reforma laboral cambió el cálculo del aguinaldo?</summary><p>No. Sigue siendo el 50% de la mayor remuneración mensual del semestre. Lo que cambió es la clasificación de algunos conceptos, como los beneficios sociales, así que conviene revisar qué incluye tu mejor sueldo.</p></details>
  <details><summary>¿El aguinaldo paga Ganancias?</summary><p>Si tu sueldo está alcanzado por Ganancias de cuarta categoría, el aguinaldo se suma a la base y puede aumentar la retención. Esta calculadora no incluye ese impuesto.</p></details>
  <details><summary>¿Qué pasa con el aguinaldo si renuncio o me despiden?</summary><p>Cobrás la parte proporcional a los días trabajados del semestre, junto con la liquidación final.</p></details>
</article>
</main>

<footer>
  <p>Los resultados son orientativos y no reemplazan tu recibo de sueldo ni el asesoramiento legal o contable. Actualizado: octubre de 2026.</p>
</footer>
</div>

<script>
const $ = id => document.getElementById(id);
const money = n => n.toLocaleString('es-AR', {style:'currency', currency:'ARS'});
const DAY = 864e5;
const utc = s => { const [a,b,c] = s.split('-').map(Number); return Date.UTC(a, b-1, c); };
const iso = t => new Date(t).toISOString().slice(0,10);

function parseMoney(s){
  s = s.replace(/[^\d.,]/g,'');
  if(!s) return NaN;
  if(s.includes(',')) s = s.replace(/\./g,'').replace(',','.');
  else if(/^\d{1,3}(\.\d{3})+$/.test(s)) s = s.replace(/\./g,'');
  return parseFloat(s);
}
function semestre(){
  const y = +$('anio').value || new Date().getFullYear(), s = $('sem').value;
  const start = Date.UTC(y, s==='1'?0:6, 1), end = Date.UTC(y, s==='1'?5:11, s==='1'?30:31);
  return {y, s, start, end, total:(end-start)/DAY+1};
}
function syncFechas(){
  const m = semestre();
  $('desde').min = $('hasta').min = iso(m.start);
  $('desde').max = $('hasta').max = iso(m.end);
  if(!$('parcial').checked){ $('desde').value = iso(m.start); $('hasta').value = iso(m.end); }
}
function ids(list, v){ list.forEach(i => $(i).textContent = v); }

function calcular(){
  const m = semestre();
  $('pago').textContent = 'Fecha de pago: hasta el ' + (m.s==='1' ? '30 de junio' : '18 de diciembre') + ' de ' + m.y + ', más cuatro días hábiles de plazo.';
  let d0 = m.start, d1 = m.end, error = '';
  if($('parcial').checked){
    const v0 = $('desde').value ? utc($('desde').value) : m.start;
    const v1 = $('hasta').value ? utc($('hasta').value) : m.end;
    if(v1 < v0) error = 'La fecha de salida es anterior a la de ingreso.';
    d0 = Math.max(m.start, v0); d1 = Math.min(m.end, v1);
  }
  $('err').hidden = !error; $('err').textContent = error;
  const dias = Math.max(0, (d1-d0)/DAY+1);
  const sueldo = parseMoney($('sueldo').value);
  $('rdias').textContent = 'Días trabajados: ' + dias + ' de ' + m.total;
  if(!(sueldo > 0) || error){
    ids(['r1','r2','r3','r4','d1','d2','d3','d4','neto'], '—');
    return;
  }
  const bruto = sueldo / 2 * dias / m.total;
  $('r1').textContent = money(sueldo);
  $('r2').textContent = money(sueldo/2);
  $('r3').textContent = (dias/m.total*100).toFixed(1).replace('.',',').replace(',0','') + '%';
  $('r4').textContent = money(bruto);
  $('d1').textContent = '-' + money(bruto*.11);
  $('d2').textContent = '-' + money(bruto*.03);
  $('d3').textContent = '-' + money(bruto*.03);
  $('d4').textContent = '-' + money(bruto*.17);
  $('neto').textContent = money(bruto*.83);
}

// Valores iniciales: semestre en curso
const hoy = new Date();
const links = [...document.querySelectorAll('#donar .monto')];
$('donar').hidden = links.some(a => a.getAttribute('href').includes('REEMPLAZAR'));
$('anio').value = hoy.getFullYear();
$('sem').value = hoy.getMonth() >= 6 ? '2' : '1';
syncFechas(); calcular();

['sem','anio'].forEach(i => $(i).addEventListener('input', () => { syncFechas(); calcular(); }));
['sueldo','desde','hasta'].forEach(i => $(i).addEventListener('input', calcular));
$('parcial').addEventListener('change', e => {
  $('fechas').classList.toggle('on', e.target.checked);
  syncFechas(); calcular();
});
$('sueldo').addEventListener('blur', e => {
  const n = parseMoney(e.target.value);
  if(n > 0) e.target.value = n.toLocaleString('es-AR', {maximumFractionDigits:2});
});
</script>
</body>
</html>
