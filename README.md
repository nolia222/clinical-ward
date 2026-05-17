<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Clinical Deterioration — Bedside Micro-Learning</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=DM+Mono:wght@400;600;700&family=DM+Sans:wght@400;500;700;800;900&display=swap');

:root {
–red: #E63946;
–blue: #1D6FA4;
–green: #2A9D6F;
–purple: #7B2FBE;
–orange: #F4A261;
–yellow: #FFD166;
–bg: #F0F4F8;
–white: #ffffff;
–dark: #1a1a2e;
}

- { margin: 0; padding: 0; box-sizing: border-box; }

body {
background: var(–bg);
font-family: ‘DM Sans’, sans-serif;
min-height: 100vh;
color: var(–dark);
}

/* ── Header ── */
.header {
background: var(–red);
padding: 0;
}
.header-top {
padding: 14px 20px 10px;
display: flex;
align-items: center;
justify-content: space-between;
}
.header-title {
color: #fff;
font-size: 16px;
font-weight: 900;
letter-spacing: 0.02em;
text-transform: uppercase;
}
.header-sub {
color: rgba(255,255,255,0.8);
font-size: 10px;
margin-top: 2px;
}
.header-badge {
background: rgba(255,255,255,0.2);
border: 1.5px solid rgba(255,255,255,0.4);
color: #fff;
font-size: 10px;
font-weight: 700;
padding: 4px 10px;
border-radius: 20px;
font-family: ‘DM Mono’, monospace;
white-space: nowrap;
}

/* ── Tagline banner ── */
.tagline {
background: var(–yellow);
padding: 10px 20px;
display: flex;
align-items: center;
gap: 10px;
}
.tagline-icon { font-size: 20px; }
.tagline-text {
font-size: 13px;
font-weight: 800;
color: #333;
line-height: 1.3;
}
.tagline-text span { color: var(–red); }

/* ── Flow bar ── */
.flow-bar {
background: var(–dark);
padding: 10px 20px;
display: flex;
align-items: center;
justify-content: center;
gap: 8px;
flex-wrap: wrap;
}
.flow-step { font-family: ‘DM Mono’, monospace; font-size: 11px; font-weight: 600; color: #fff; }
.flow-arrow { color: var(–orange); font-size: 13px; }
.flow-step.hl { color: var(–yellow); font-weight: 800; }

/* ── Cards section ── */
.cards-section {
padding: 20px 14px 40px;
}
.section-hint {
text-align: center;
font-size: 10px;
font-weight: 700;
letter-spacing: 0.1em;
text-transform: uppercase;
color: #999;
margin-bottom: 14px;
}
.cards-grid {
display: grid;
grid-template-columns: 1fr 1fr;
gap: 12px;
max-width: 560px;
margin: 0 auto;
}

/* ── Card ── */
.card {
border-radius: 14px;
overflow: hidden;
cursor: pointer;
box-shadow: 0 4px 16px rgba(0,0,0,0.12);
transition: transform 0.18s, box-shadow 0.18s;
border: 2.5px solid transparent;
}
.card:hover { transform: translateY(-4px); box-shadow: 0 10px 28px rgba(0,0,0,0.18); }
.card:active { transform: scale(0.97); }
.card-1 { border-color: var(–blue); }
.card-2 { border-color: var(–green); }
.card-3 { border-color: var(–purple); }
.card-4 { border-color: var(–red); }

.card-header {
padding: 12px 14px 10px;
display: flex;
align-items: center;
gap: 10px;
}
.card-1 .card-header { background: var(–blue); }
.card-2 .card-header { background: var(–green); }
.card-3 .card-header { background: var(–purple); }
.card-4 .card-header { background: var(–red); }

.card-icon { font-size: 22px; }
.card-num {
font-family: ‘DM Mono’, monospace;
font-size: 8px;
color: rgba(255,255,255,0.65);
font-weight: 600;
letter-spacing: 0.1em;
text-transform: uppercase;
}
.card-title { font-size: 12px; font-weight: 800; color: #fff; line-height: 1.2; margin-top: 1px; }

.card-body {
background: var(–white);
padding: 10px 14px 12px;
}
.card-desc { font-size: 9.5px; color: #555; line-height: 1.5; }
.card-tap {
margin-top: 8px;
font-size: 9px;
font-weight: 700;
letter-spacing: 0.08em;
text-transform: uppercase;
}
.card-1 .card-tap { color: var(–blue); }
.card-2 .card-tap { color: var(–green); }
.card-3 .card-tap { color: var(–purple); }
.card-4 .card-tap { color: var(–red); }

/* ── Modal ── */
.modal-overlay {
display: none;
position: fixed;
inset: 0;
background: rgba(0,0,0,0.6);
z-index: 200;
align-items: flex-end;
justify-content: center;
}
.modal-overlay.open { display: flex; }
.modal {
background: var(–white);
border-radius: 20px 20px 0 0;
width: 100%;
max-width: 580px;
max-height: 90vh;
overflow-y: auto;
animation: slideUp 0.3s cubic-bezier(0.34,1.4,0.64,1);
}
@keyframes slideUp { from { transform: translateY(100%); opacity: 0; } to { transform: translateY(0); opacity: 1; } }

.modal-header {
padding: 16px 20px;
display: flex;
align-items: center;
justify-content: space-between;
position: sticky;
top: 0;
z-index: 10;
}
.m1 .modal-header { background: var(–blue); }
.m2 .modal-header { background: var(–green); }
.m3 .modal-header { background: var(–purple); }
.m4 .modal-header { background: var(–red); }
.modal-title { font-size: 14px; font-weight: 800; color: #fff; }
.modal-close { width: 28px; height: 28px; background: rgba(255,255,255,0.2); border: none; border-radius: 50%; color: #fff; font-size: 15px; cursor: pointer; display: flex; align-items: center; justify-content: center; font-weight: 700; }

.modal-body { padding: 16px 20px 36px; }

/* ── Tagline inside modal ── */
.modal-tagline {
background: var(–yellow);
border-radius: 10px;
padding: 10px 14px;
margin-bottom: 14px;
font-size: 12px;
font-weight: 800;
color: #333;
display: flex;
align-items: center;
gap: 8px;
}

/* section label */
.slabel {
font-size: 9px;
font-weight: 700;
letter-spacing: 0.12em;
text-transform: uppercase;
color: #aaa;
margin: 14px 0 7px;
}
.slabel:first-child { margin-top: 0; }

/* V/S boxes */
.vs-grid { display: grid; grid-template-columns: repeat(4,1fr); gap: 6px; margin-bottom: 10px; }
.vs-box { border-radius: 10px; padding: 8px 4px; text-align: center; }
.vs-box.rr { background: #DBEAFE; }
.vs-box.hr { background: #FCE7F3; }
.vs-box.spo { background: #D1FAE5; }
.vs-box.bp { background: #FEF3C7; }
.vs-name { font-family: ‘DM Mono’, monospace; font-size: 12px; font-weight: 700; color: var(–dark); }
.vs-range { font-family: ‘DM Mono’, monospace; font-size: 9px; color: var(–green); font-weight: 600; margin-top: 2px; }

.rule-box {
background: #FFF7ED;
border-left: 5px solid var(–orange);
border-radius: 10px;
padding: 10px 14px;
margin-bottom: 8px;
}
.rule-text { font-size: 14px; font-weight: 800; color: #7B3F00; }
.rule-text span { color: var(–red); font-size: 18px; }
.rule-sub { font-size: 9.5px; color: #7B3F00; margin-top: 3px; line-height: 1.5; }

/* SBAR */
.sbar-list { display: flex; flex-direction: column; gap: 8px; }
.sbar-row { display: grid; grid-template-columns: 16px 1fr; gap: 0 10px; align-items: start; }
.sl { font-family: ‘DM Mono’, monospace; font-size: 16px; font-weight: 700; line-height: 1.2; }
.sc { font-size: 10px; color: #333; line-height: 1.65; }
.sc strong { font-weight: 800; font-size: 11px; display: block; margin-bottom: 1px; }
.sc em { color: #888; font-style: italic; font-size: 9px; }
.concerned { display: block; font-weight: 800; color: var(–red); font-size: 11px; margin-top: 3px; }

/* Pathway */
.pathway { display: flex; flex-direction: column; }
.p-step { display: flex; align-items: flex-start; gap: 12px; border-radius: 10px; padding: 10px 12px; margin-bottom: 0; }
.p1 { background: #DBEAFE; }
.p2 { background: #D1FAE5; }
.p3 { background: #EDE9FE; }
.p4 { background: #FEE2E2; }
.p-icon { font-size: 22px; flex-shrink: 0; }
.p-title { font-size: 11px; font-weight: 800; color: var(–dark); }
.p-sub { font-size: 9px; color: #555; margin-top: 2px; line-height: 1.5; }
.p-arrow { text-align: center; font-size: 22px; color: #ccc; padding: 2px 0; }

/* Flags */
.flags { display: flex; flex-direction: column; gap: 7px; }
.flag { display: flex; align-items: flex-start; gap: 10px; border-radius: 10px; padding: 9px 12px; border-left: 4px solid; }
.f1 { background: #EFF6FF; border-left-color: var(–blue); }
.f2 { background: #FEF2F2; border-left-color: var(–red); }
.f3 { background: #F5F3FF; border-left-color: var(–purple); }
.f4 { background: #FFF7ED; border-left-color: var(–orange); }
.f5 { background: #FFFBEB; border-left-color: var(–yellow); }
.flag-icon { font-size: 18px; flex-shrink: 0; margin-top: 1px; }
.flag-text { font-size: 10px; color: #333; line-height: 1.55; }
.flag-text strong { font-size: 11px; font-weight: 800; display: block; margin-bottom: 1px; color: var(–dark); }

/* Pull */
.pull {
background: var(–dark);
color: #fff;
border-radius: 10px;
padding: 12px 14px;
font-size: 10.5px;
line-height: 1.6;
margin-top: 14px;
}
.pull strong { color: var(–yellow); font-size: 12px; display: block; margin-bottom: 4px; }
</style>

</head>
<body>

<!-- Header -->

<div class="header">
  <div class="header-top">
    <div>
      <div class="header-title">⚡ Clinical Deterioration</div>
      <div class="header-sub">Surgical Ward · Bedside Micro-Learning</div>
    </div>
    <div class="header-badge">If ≥2 V/S → Escalate</div>
  </div>

  <!-- Tagline -->

  <div class="tagline">
    <span class="tagline-icon">⚠️</span>
    <div class="tagline-text">
      <span>Delaying escalation increases workload later.</span><br>
      <span style="font-weight:500; font-size:11px; color:#555;">A 30-second call now prevents hours of crisis management.</span>
    </div>
  </div>

  <!-- Flow -->

  <div class="flow-bar">
    <span class="flow-step">≥2 V/S Abnormal</span>
    <span class="flow-arrow">→</span>
    <span class="flow-step">Assess</span>
    <span class="flow-arrow">→</span>
    <span class="flow-step">SBAR</span>
    <span class="flow-arrow">→</span>
    <span class="flow-step hl">Escalate Now</span>
  </div>
</div>

<!-- Cards -->

<div class="cards-section">
  <div class="section-hint">Tap a card to open</div>
  <div class="cards-grid">

```
<div class="card card-1" onclick="openModal('m1')">
  <div class="card-header">
    <span class="card-icon">🔍</span>
    <div><div class="card-num">Step 01</div><div class="card-title">Recognise Deterioration</div></div>
  </div>
  <div class="card-body">
    <div class="card-desc">V/S normal ranges + ≥2 abnormal rule</div>
    <div class="card-tap">Tap to open →</div>
  </div>
</div>

<div class="card card-2" onclick="openModal('m2')">
  <div class="card-header">
    <span class="card-icon">📋</span>
    <div><div class="card-num">Step 02</div><div class="card-title">SBAR — Say This Now</div></div>
  </div>
  <div class="card-body">
    <div class="card-desc">Full SBAR with examples ready to say</div>
    <div class="card-tap">Tap to open →</div>
  </div>
</div>

<div class="card card-3" onclick="openModal('m3')">
  <div class="card-header">
    <span class="card-icon">⚡</span>
    <div><div class="card-num">Step 03</div><div class="card-title">Response Pathway</div></div>
  </div>
  <div class="card-body">
    <div class="card-desc">4 steps from detection to action</div>
    <div class="card-tap">Tap to open →</div>
  </div>
</div>

<div class="card card-4" onclick="openModal('m4')">
  <div class="card-header">
    <span class="card-icon">🚨</span>
    <div><div class="card-num">Step 04</div><div class="card-title">Red Flags — Call MET Now</div></div>
  </div>
  <div class="card-body">
    <div class="card-desc">Critical signs requiring immediate MET call</div>
    <div class="card-tap">Tap to open →</div>
  </div>
</div>
```

  </div>
</div>

<!-- MODAL 1 -->

<div class="modal-overlay" id="overlay-m1" onclick="closeModal('m1')">
  <div class="modal m1" onclick="event.stopPropagation()">
    <div class="modal-header"><span class="modal-title">🔍 Recognise Deterioration</span><button class="modal-close" onclick="closeModal('m1')">✕</button></div>
    <div class="modal-body">
      <div class="modal-tagline">⚠️ Delaying escalation increases your workload later.</div>
      <div class="slabel">V/S Normal Ranges</div>
      <div class="vs-grid">
        <div class="vs-box rr"><div class="vs-name">RR</div><div class="vs-range">12–20/min</div></div>
        <div class="vs-box hr"><div class="vs-name">HR</div><div class="vs-range">60–100 bpm</div></div>
        <div class="vs-box spo"><div class="vs-name">SpO₂</div><div class="vs-range">≥ 95%</div></div>
        <div class="vs-box bp"><div class="vs-name">SBP</div><div class="vs-range">90–140 mmHg</div></div>
      </div>
      <div class="rule-box">
        <div class="rule-text"><span>≥2</span> V/S outside range = Patient at risk</div>
        <div class="rule-sub">In a surgical ward — do not wait to find out why.<br>Escalate because you don't know why yet.</div>
      </div>
      <div class="pull">
        <strong>Why 2 and not wait for NEWS2=5?</strong>
        Research shows mortality increases in a stepwise manner with each additional abnormal vital sign. Up to 4 hours before cardiac arrest, 59.4% of patients already have ≥1 abnormal vital sign. The signal is there at 2 — act on it.
        <br><br><span style="font-size:9px; color:#aaa;">WARD-AMS Trial, 2025 · Strand et al., 2025</span>
      </div>
    </div>
  </div>
</div>

<!-- MODAL 2 -->

<div class="modal-overlay" id="overlay-m2" onclick="closeModal('m2')">
  <div class="modal m2" onclick="event.stopPropagation()">
    <div class="modal-header"><span class="modal-title">📋 SBAR — Say This Now</span><button class="modal-close" onclick="closeModal('m2')">✕</button></div>
    <div class="modal-body">
      <div class="modal-tagline">⚠️ You are not diagnosing — you are escalating.</div>
      <div class="slabel">Say This In Order</div>
      <div class="sbar-list">
        <div class="sbar-row">
          <span class="sl" style="color:var(--blue);">S</span>
          <span class="sc"><strong>Situation</strong>📞 "Mr/Ms [Name], [Age] y/o — I am concerned."</span>
        </div>
        <div class="sbar-row">
          <span class="sl" style="color:var(--green);">B</span>
          <span class="sc"><strong>Background</strong>🗓️ Post-op day [X] · Dx: [X]<br>💊 Meds: [X] · 🔬 Labs: [X] · 🧪 Output: [X] ml</span>
        </div>
        <div class="sbar-row">
          <span class="sl" style="color:var(--purple);">A</span>
          <span class="sc">
            <strong>Assessment</strong>
            RR <span style="color:var(--red);">⬆️or⬇️</span> · HR <span style="color:var(--red);">⬆️or⬇️</span> · SpO₂ <span style="color:var(--red);">⬇️</span> · BP <span style="color:var(--red);">⬆️or⬇️</span><br>
            🩺 <em>ex: O₂ given · IV fluids · Dr notified</em>
            <span class="concerned">2+ outside range = Concerned ⚠️</span>
          </span>
        </div>
        <div class="sbar-row">
          <span class="sl" style="color:var(--red);">R</span>
          <span class="sc"><strong>Recommendation</strong>👁️ "Please come and review immediately."</span>
        </div>
      </div>
      <div class="pull">
        <strong>Your concern is enough reason to call.</strong>
        Say what you see and ask for help. The SBAR gives you structure so you feel confident — not panicked.
      </div>
    </div>
  </div>
</div>

<!-- MODAL 3 -->

<div class="modal-overlay" id="overlay-m3" onclick="closeModal('m3')">
  <div class="modal m3" onclick="event.stopPropagation()">
    <div class="modal-header"><span class="modal-title">⚡ Response Pathway</span><button class="modal-close" onclick="closeModal('m3')">✕</button></div>
    <div class="modal-body">
      <div class="modal-tagline">⚠️ Early escalation reduces future workload.</div>
      <div class="slabel">Follow These Steps — In Order</div>
      <div class="pathway">
        <div class="p-step p1"><span class="p-icon">👁️</span><div><div class="p-title">Identify ≥2 Abnormal V/S</div><div class="p-sub">Do not document and move on — this is your trigger to act now.</div></div></div>
        <div class="p-arrow">↓</div>
        <div class="p-step p2"><span class="p-icon">🩺</span><div><div class="p-title">Go to Bedside — Assess Now</div><div class="p-sub">Check consciousness · repeat full V/S · look at the patient.</div></div></div>
        <div class="p-arrow">↓</div>
        <div class="p-step p3"><span class="p-icon">📞</span><div><div class="p-title">Call & Use SBAR</div><div class="p-sub">Escalate to doctor or MET/RRT · use SBAR to structure your call.</div></div></div>
        <div class="p-arrow">↓</div>
        <div class="p-step p4"><span class="p-icon">💊</span><div><div class="p-title">Act, Monitor & Document</div><div class="p-sub">Implement orders · continue close monitoring · document everything.</div></div></div>
      </div>
      <div class="pull">
        <strong>A 30-second call now prevents hours of crisis management later.</strong>
        Early escalation = less workload, better outcomes, safer patients.
        <br><br><span style="font-size:9px;color:#aaa;">Bowles et al., 2024 — each hour of delay independently increases mortality risk.</span>
      </div>
    </div>
  </div>
</div>

<!-- MODAL 4 -->

<div class="modal-overlay" id="overlay-m4" onclick="closeModal('m4')">
  <div class="modal m4" onclick="event.stopPropagation()">
    <div class="modal-header"><span class="modal-title">🚨 Red Flags — Call MET Now</span><button class="modal-close" onclick="closeModal('m4')">✕</button></div>
    <div class="modal-body">
      <div class="modal-tagline">🚨 These signs = Call MET / RRT immediately.</div>
      <div class="flags">
        <div class="flag f1"><span class="flag-icon">🫁</span><div class="flag-text"><strong>Airway / Breathing</strong>RR &lt;8 or &gt;30 · SpO₂ &lt;90% despite O₂ · stridor</div></div>
        <div class="flag f2"><span class="flag-icon">❤️</span><div class="flag-text"><strong>Circulation</strong>SBP &lt;90 mmHg · HR &gt;130 or &lt;40 · no urine output · cold skin</div></div>
        <div class="flag f3"><span class="flag-icon">🧠</span><div class="flag-text"><strong>Neurology</strong>Sudden confusion · unresponsive · new seizure · GCS drop</div></div>
        <div class="flag f4"><span class="flag-icon">🩸</span><div class="flag-text"><strong>Surgical Concern</strong>Sudden abdominal pain · wound dehiscence · heavy bleeding</div></div>
        <div class="flag f5"><span class="flag-icon">⚠️</span><div class="flag-text"><strong>Any Doubt?</strong>Trust your instinct — escalate. Delay costs more than a call.</div></div>
      </div>
      <div class="pull">
        <strong>In a surgical ward: fever + low BP ≠ "just dehydration."</strong>
        It could be sepsis, anastomotic leak, or internal bleeding. Don't wait to find out which. Call now — let the doctor decide.
      </div>
    </div>
  </div>
</div>

<script>
  function openModal(id) { document.getElementById('overlay-' + id).classList.add('open'); document.body.style.overflow = 'hidden'; }
  function closeModal(id) { document.getElementById('overlay-' + id).classList.remove('open'); document.body.style.overflow = ''; }
  document.addEventListener('keydown', function(e) { if (e.key === 'Escape') ['m1','m2','m3','m4'].forEach(closeModal); });
</script>

</body>
</html>
