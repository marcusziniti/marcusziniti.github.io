# marcusziniti.github.io
A collection of Marcus Ziniti's projects and accomplishments!
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Jordan Reyes — Mechanical Engineer</title>
<meta name="description" content="Mechanical engineering portfolio — design, analysis, and manufacturing projects.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=IBM+Plex+Mono:wght@400;500;600;700&family=IBM+Plex+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
<style>
  /* ============================================================
     EDIT ZONE: search for "EDIT:" comments to find every place
     you should swap in your own name, projects, links, etc.
     ============================================================ */

  :root{
    --blueprint:      #17324f;   /* cyanotype blueprint blue — frame, nav, footer */
    --blueprint-deep:  #0f2438;
    --blueprint-line: #bcd6ea;   /* light linework on blueprint bg */
    --paper:          #edefe9;   /* drafting vellum — content background */
    --paper-raised:   #f7f8f4;   /* card surface, slightly lighter than paper */
    --ink:            #1e2731;   /* primary text on paper */
    --graphite:       #5c6773;   /* secondary text, dimension lines, hairlines */
    --graphite-faint: #aeb6bd;
    --orange:         #d9581f;   /* safety orange — accent, CTAs */
    --orange-dim:     #b8481a;
    --cyan:           #4f88ab;   /* grid lines, tags */
    --radius: 2px;
    --frame: 14px;
    --mono: 'IBM Plex Mono', ui-monospace, monospace;
    --sans: 'IBM Plex Sans', -apple-system, sans-serif;
  }

  *{ box-sizing:border-box; margin:0; padding:0; }
  html{ scroll-behavior:smooth; }
  @media (prefers-reduced-motion: reduce){ html{ scroll-behavior:auto; } *{ animation:none !important; transition:none !important; } }

  body{
    font-family:var(--sans);
    background:var(--blueprint);
    color:var(--ink);
    line-height:1.6;
    -webkit-font-smoothing:antialiased;
  }

  a{ color:inherit; }
  ::selection{ background:var(--orange); color:#fff; }

  /* ---------- drawing-sheet frame ---------- */
  .sheet-frame{
    position:fixed; inset:0; pointer-events:none; z-index:80;
    border:var(--frame) solid var(--blueprint);
  }
  .sheet-frame::before{
    content:""; position:absolute; inset:var(--frame);
    border:1px solid var(--blueprint-line);
    opacity:.55;
  }
  .zone-row{
    position:fixed; left:var(--frame); right:var(--frame);
    display:flex; justify-content:space-between;
    font-family:var(--mono); font-size:10px; letter-spacing:.12em;
    color:var(--blueprint-line); opacity:.8; z-index:81; pointer-events:none;
    padding:0 6px;
  }
  .zone-row.top{ top:0; height:var(--frame); align-items:center; }
  .zone-row.bottom{ bottom:0; height:var(--frame); align-items:center; }
  .zone-col{
    position:fixed; top:var(--frame); bottom:var(--frame);
    display:flex; flex-direction:column; justify-content:space-between;
    font-family:var(--mono); font-size:10px; letter-spacing:.12em;
    color:var(--blueprint-line); opacity:.8; z-index:81; pointer-events:none;
    padding:6px 0;
  }
  .zone-col.left{ left:0; width:var(--frame); align-items:center; }
  .zone-col.right{ right:0; width:var(--frame); align-items:center; }
  .zone-col span, .zone-row span{ writing-mode:horizontal-tb; }
  .zone-col.left span, .zone-col.right span{ writing-mode:vertical-rl; }

  @media (max-width: 720px){
    :root{ --frame: 8px; }
    .zone-row, .zone-col{ display:none; }
  }

  /* ---------- title block (fixed, bottom-right) ---------- */
  .title-block{
    position:fixed; right:var(--frame); bottom:var(--frame);
    z-index:90; background:var(--blueprint);
    border:1px solid var(--blueprint-line);
    font-family:var(--mono); font-size:10px; color:var(--blueprint-line);
    display:grid; grid-template-columns:auto auto;
    min-width:220px;
  }
  .title-block div{ padding:4px 8px; border-top:1px solid rgba(188,214,234,.35); border-left:1px solid rgba(188,214,234,.35); }
  .title-block div:nth-child(-n+2){ border-top:none; }
  .title-block .label{ color:var(--blueprint-line); opacity:.6; border-left:none; }
  .title-block .val{ color:#fff; text-align:right; }
  @media (max-width: 720px){ .title-block{ display:none; } }

  /* ---------- nav ---------- */
  header.nav{
    position:sticky; top:0; z-index:70;
    background:var(--blueprint-deep);
    border-bottom:1px solid var(--blueprint-line);
    margin:var(--frame) var(--frame) 0;
  }
  .nav-inner{
    max-width:1180px; margin:0 auto; padding:14px 24px;
    display:flex; align-items:center; justify-content:space-between; gap:16px;
  }
  .nav-mark{ font-family:var(--mono); font-weight:700; color:#fff; font-size:14px; letter-spacing:.04em; }
  .nav-mark small{ display:block; font-weight:400; font-size:10px; color:var(--blueprint-line); letter-spacing:.16em; margin-top:2px;}
  .nav-links{ display:flex; gap:22px; font-family:var(--mono); font-size:12px; letter-spacing:.06em; }
  .nav-links a{ text-decoration:none; color:var(--blueprint-line); position:relative; padding-bottom:3px; }
  .nav-links a:hover{ color:#fff; }
  .nav-links a::after{ content:""; position:absolute; left:0; bottom:0; height:1px; width:0; background:var(--orange); transition:width .2s ease; }
  .nav-links a:hover::after{ width:100%; }
  @media (max-width: 640px){ .nav-links{ display:none; } }

  main{ background:var(--paper); margin:0 var(--frame) var(--frame); }
  .wrap{ max-width:1180px; margin:0 auto; padding:0 24px; }

  section{ padding:96px 0; border-bottom:1px solid #d8d5c8; }
  section:last-of-type{ border-bottom:none; }

  .eyebrow{
    font-family:var(--mono); font-size:11px; letter-spacing:.2em; text-transform:uppercase;
    color:var(--orange); display:flex; align-items:center; gap:10px; margin-bottom:18px;
  }
  .eyebrow::before{ content:""; width:22px; height:1px; background:var(--orange); }

  h1,h2,h3{ font-family:var(--mono); font-weight:700; color:var(--ink); letter-spacing:-.01em; }

  /* ---------- hero ---------- */
  .hero{ padding-top:64px; }
  .hero h1{ font-size:clamp(34px,6vw,64px); line-height:1.05; max-width:14ch; }
  .hero h1 em{ font-style:normal; color:var(--orange); }
  .hero p.lede{ font-size:18px; color:var(--graphite); max-width:52ch; margin-top:22px; }
  .hero-meta{
    margin-top:44px; display:grid; grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
    gap:0; border-top:1px solid var(--graphite-faint);
  }
  .hero-meta div{ padding:14px 0; border-right:1px solid var(--graphite-faint); padding-right:16px; }
  .hero-meta div:last-child{ border-right:none; }
  .hero-meta .k{ font-family:var(--mono); font-size:10px; letter-spacing:.14em; color:var(--graphite); text-transform:uppercase; }
  .hero-meta .v{ font-family:var(--mono); font-size:15px; color:var(--ink); margin-top:6px; font-weight:600; }
  .cta-row{ margin-top:36px; display:flex; gap:14px; flex-wrap:wrap; }
  .btn{
    font-family:var(--mono); font-size:12px; letter-spacing:.08em; text-transform:uppercase;
    text-decoration:none; padding:12px 22px; border:1px solid var(--ink); color:var(--ink);
    display:inline-flex; align-items:center; gap:8px; transition:background .15s, color .15s;
  }
  .btn.primary{ background:var(--orange); border-color:var(--orange); color:#fff; }
  .btn.primary:hover{ background:var(--orange-dim); border-color:var(--orange-dim); }
  .btn:not(.primary):hover{ background:var(--ink); color:var(--paper); }

  /* ---------- about ---------- */
  .about-grid{ display:grid; grid-template-columns:1.1fr .9fr; gap:64px; }
  @media (max-width:820px){ .about-grid{ grid-template-columns:1fr; gap:36px; } }
  .about-grid p{ color:var(--graphite); max-width:60ch; }
  .about-grid p + p{ margin-top:14px; }
  .spec-list{ font-family:var(--mono); font-size:13px; }
  .spec-list li{ list-style:none; display:flex; justify-content:space-between; padding:10px 0; border-bottom:1px dashed var(--graphite-faint); }
  .spec-list .k{ color:var(--graphite); }
  .spec-list .v{ color:var(--ink); font-weight:600; text-align:right; }

  /* ---------- projects / BOM table ---------- */
  .bom-head{ display:flex; align-items:baseline; justify-content:space-between; margin-bottom:28px; flex-wrap:wrap; gap:10px;}
  table.bom{ width:100%; border-collapse:collapse; font-family:var(--mono); font-size:13px; }
  table.bom thead th{
    text-align:left; font-size:10px; letter-spacing:.14em; text-transform:uppercase; color:var(--graphite);
    border-bottom:1px solid var(--ink); padding:0 10px 10px;
  }
  table.bom tbody tr{ cursor:pointer; border-bottom:1px solid var(--graphite-faint); }
  table.bom tbody tr:hover{ background:rgba(217,88,31,.06); }
  table.bom td{ padding:16px 10px; vertical-align:top; }
  table.bom td.item{ color:var(--orange); font-weight:700; width:54px; }
  table.bom td.name{ color:var(--ink); font-weight:600; }
  table.bom td.name .sub{ display:block; color:var(--graphite); font-weight:400; font-size:12px; margin-top:3px; font-family:var(--sans); }
  table.bom td.mat, table.bom td.qty{ color:var(--graphite); white-space:nowrap; }
  table.bom td.chevron{ text-align:right; color:var(--graphite-faint); width:24px; }
  tr.bom-row.open .chevron{ color:var(--orange); }

  .bom-detail{ display:none; background:var(--paper-raised); border-left:3px solid var(--orange); }
  .bom-detail.open{ display:table-row; }
  .bom-detail td{ padding:22px 10px 30px 10px; font-family:var(--sans); }
  .bom-detail .detail-grid{ display:grid; grid-template-columns:2fr 1fr; gap:32px; }
  @media (max-width:720px){ .bom-detail .detail-grid{ grid-template-columns:1fr; } }
  .bom-detail p{ color:var(--graphite); font-size:14px; max-width:64ch; }
  .bom-detail h4{ font-family:var(--mono); font-size:11px; letter-spacing:.1em; text-transform:uppercase; color:var(--ink); margin-bottom:10px; margin-top:18px; }
  .bom-detail h4:first-child{ margin-top:0; }
  .taglist{ display:flex; flex-wrap:wrap; gap:8px; }
  .tag{
    font-family:var(--mono); font-size:11px; padding:4px 9px; border:1px solid var(--cyan); color:var(--cyan);
    border-radius:var(--radius);
  }
  .result-list li{ font-size:13px; color:var(--graphite); list-style:none; padding-left:16px; position:relative; margin-top:6px; }
  .result-list li::before{ content:"→"; position:absolute; left:0; color:var(--orange); }

  /* ---------- skills ---------- */
  .skills-grid{ display:grid; grid-template-columns:repeat(auto-fit,minmax(230px,1fr)); gap:36px; }
  .skill-group h3{ font-size:13px; letter-spacing:.1em; text-transform:uppercase; margin-bottom:16px; display:flex; align-items:center; gap:8px; }
  .skill-group h3::before{ content:"◇"; color:var(--orange); font-size:11px; }
  .skill-chip-row{ display:flex; flex-wrap:wrap; gap:8px; }
  .chip{
    font-family:var(--mono); font-size:12px; padding:7px 11px; background:var(--paper-raised);
    border:1px solid var(--graphite-faint); color:var(--ink);
  }

  /* ---------- experience timeline ---------- */
  .timeline{ position:relative; padding-left:26px; }
  .timeline::before{ content:""; position:absolute; left:6px; top:6px; bottom:6px; width:1px; background:var(--graphite-faint); }
  .tl-item{ position:relative; padding-bottom:40px; }
  .tl-item:last-child{ padding-bottom:0; }
  .tl-item::before{ content:""; position:absolute; left:-26px; top:4px; width:9px; height:9px; background:var(--orange); border:2px solid var(--paper); outline:1px solid var(--orange); border-radius:50%; }
  .tl-date{ font-family:var(--mono); font-size:11px; letter-spacing:.1em; color:var(--orange); text-transform:uppercase; }
  .tl-role{ font-family:var(--mono); font-size:17px; font-weight:700; margin-top:6px; }
  .tl-org{ color:var(--graphite); font-size:13px; margin-top:2px; }
  .tl-desc{ color:var(--graphite); font-size:14px; margin-top:10px; max-width:60ch; }

  /* ---------- contact ---------- */
  .contact-block{ display:flex; justify-content:space-between; align-items:flex-end; flex-wrap:wrap; gap:32px; }
  .contact-block h2{ font-size:clamp(28px,4.5vw,44px); max-width:12ch; line-height:1.1; }
  .contact-links{ display:flex; flex-direction:column; gap:10px; font-family:var(--mono); font-size:14px; }
  .contact-links a{ text-decoration:none; border-bottom:1px solid transparent; }
  .contact-links a:hover{ border-color:var(--orange); color:var(--orange); }

  footer.foot{
    background:var(--blueprint-deep); color:var(--blueprint-line);
    margin:0 var(--frame) var(--frame); padding:20px 24px;
    display:flex; justify-content:space-between; flex-wrap:wrap; gap:8px;
    font-family:var(--mono); font-size:11px; letter-spacing:.06em;
  }
  footer.foot a{ color:#fff; text-decoration:none; }
</style>
</head>
<body>

<div class="sheet-frame" aria-hidden="true"></div>
<div class="zone-row top" aria-hidden="true"><span>A</span><span>B</span><span>C</span><span>D</span><span>E</span><span>F</span></div>
<div class="zone-row bottom" aria-hidden="true"><span>A</span><span>B</span><span>C</span><span>D</span><span>E</span><span>F</span></div>
<div class="zone-col left" aria-hidden="true"><span>1</span><span>2</span><span>3</span><span>4</span></div>
<div class="zone-col right" aria-hidden="true"><span>1</span><span>2</span><span>3</span><span>4</span></div>

<div class="title-block" aria-hidden="true">
  <div class="label">DRAWN BY</div><div class="val">J. REYES</div>
  <div class="label">SHEET</div><div class="val" id="sheet-no">01 / 06</div>
  <div class="label">REV</div><div class="val">C</div>
  <div class="label">SCALE</div><div class="val">1:1</div>
</div>

<header class="nav">
  <div class="nav-inner">
    <!-- EDIT: your name -->
    <div class="nav-mark">Marcus Ziniti<small>MECHANICAL ENGINEER</small></div>
    <nav class="nav-links">
      <a href="#about">About</a>
      <a href="#projects">Projects</a>
      <a href="#skills">Skills</a>
      <a href="#experience">Experience</a>
      <a href="#contact">Contact</a>
    </nav>
  </div>
</header>

<main>
  <div class="wrap">

    <!-- ============ HERO ============ -->
    <section class="hero" id="hero" data-sheet="01 / 06">
      <p class="eyebrow">Portfolio — Rev. C</p>
      <!-- EDIT: headline -->
      <h1>Mechanical design, from <em>sketch</em> to shipped part.</h1>
      <!-- EDIT: one or two sentence summary of what you do -->
      <p class="lede">I design and validate mechanical systems — CAD modeling, FEA/CFD analysis, and DFM for CNC and additive manufacturing — and take them from concept through tested prototype.</p>

      <div class="hero-meta">
        <div><div class="k">Based in</div><div class="v">Chicago, IL</div></div>
        <div><div class="k">Focus</div><div class="v">Product & Mechanisms</div></div>
        <div><div class="k">Tools</div><div class="v">SolidWorks / ANSYS</div></div>
        <div><div class="k">Available</div><div class="v">Open to roles</div></div>
      </div>

      <div class="cta-row">
        <!-- EDIT: link to your resume PDF and email -->
        <a class="btn primary" href="resume.pdf">Download résumé</a>
        <a class="btn" href="#projects">View projects</a>
      </div>
    </section>

    <!-- ============ ABOUT ============ -->
    <section id="about" data-sheet="02 / 06">
      <p class="eyebrow">01 — About</p>
      <div class="about-grid">
        <div>
          <!-- EDIT: your background -->
          <p>I'm a mechanical engineer focused on turning early-stage concepts into manufacturable hardware. My background spans product design, structural analysis, and hands-on prototyping — I'm equally comfortable running a FEA study and standing at a mill.</p>
          <p>Most recently I've worked on robotics actuation and thermal systems, where tolerance stack-up, material selection, and DFM decisions determine whether a design survives contact with reality.</p>
        </div>
        <ul class="spec-list">
          <li><span class="k">Education</span><span class="v">B.S. Mechanical Engineering</span></li>
          <li><span class="k">Certifications</span><span class="v">GD&T (ASME Y14.5)</span></li>
          <li><span class="k">Years experience</span><span class="v">5</span></li>
          <li><span class="k">Manufacturing</span><span class="v">CNC / FDM / SLA / Sheet metal</span></li>
          <li><span class="k">Analysis</span><span class="v">FEA, CFD, Thermal</span></li>
        </ul>
      </div>
    </section>

    <!-- ============ PROJECTS ============ -->
    <section id="projects" data-sheet="03 / 06">
      <div class="bom-head">
        <p class="eyebrow" style="margin-bottom:0;">02 — Selected work</p>
        <span style="font-family:var(--mono); font-size:11px; color:var(--graphite);">Click a row to expand — bill of materials</span>
      </div>

      <table class="bom">
        <thead>
          <tr><th>Item</th><th>Description</th><th>Material</th><th>Type</th><th></th></tr>
        </thead>
        <tbody>
          <!-- EDIT: replace each project with your own. Duplicate the two <tr> rows per project. -->
          <tr class="bom-row" data-target="p1">
            <td class="item">001</td>
            <td class="name">CNC robotic gripper<span class="sub">Underactuated 3-finger end effector</span></td>
            <td class="mat">6061-T6 Al</td>
            <td class="qty">Robotics</td>
            <td class="chevron">▾</td>
          </tr>
          <tr class="bom-detail" id="p1">
            <td colspan="5">
              <div class="detail-grid">
                <div>
                  <h4>Overview</h4>
                  <p>Designed an underactuated gripper for a pick-and-place robot arm, using a tendon-driven linkage to conform to irregular parts without added actuators. Took the design from concept sketches through tolerance analysis to a machined, tested prototype.</p>
                  <h4>Outcome</h4>
                  <ul class="result-list">
                    <li>Grip success rate improved from 71% to 96% on the target part family</li>
                    <li>Reduced part count 40% versus the previous fully-actuated design</li>
                  </ul>
                </div>
                <div>
                  <h4>Tools & process</h4>
                  <div class="taglist">
                    <span class="tag">SolidWorks</span><span class="tag">FEA</span><span class="tag">CNC Mill</span><span class="tag">GD&T</span>
                  </div>
                </div>
              </div>
            </td>
          </tr>

          <tr class="bom-row" data-target="p2">
            <td class="item">002</td>
            <td class="name">Suspension geometry study<span class="sub">Double-wishbone kinematics optimization</span></td>
            <td class="mat">4130 Steel</td>
            <td class="qty">Automotive</td>
            <td class="chevron">▾</td>
          </tr>
          <tr class="bom-detail" id="p2">
            <td colspan="5">
              <div class="detail-grid">
                <div>
                  <h4>Overview</h4>
                  <p>Modeled and optimized double-wishbone suspension geometry for a formula-style vehicle, balancing camber gain, roll center height, and bump steer across the suspension travel range.</p>
                  <h4>Outcome</h4>
                  <ul class="result-list">
                    <li>Cut bump steer by 60% over the full travel range</li>
                    <li>Delivered a full drawing package for fabrication and welding</li>
                  </ul>
                </div>
                <div>
                  <h4>Tools & process</h4>
                  <div class="taglist">
                    <span class="tag">MATLAB</span><span class="tag">Lotus Suspension</span><span class="tag">Fusion 360</span>
                  </div>
                </div>
              </div>
            </td>
          </tr>

          <tr class="bom-row" data-target="p3">
            <td class="item">003</td>
            <td class="name">3D-printed prosthetic hand<span class="sub">Low-cost body-powered device</span></td>
            <td class="mat">PETG / TPU</td>
            <td class="qty">Biomechanical</td>
            <td class="chevron">▾</td>
          </tr>
          <tr class="bom-detail" id="p3">
            <td colspan="5">
              <div class="detail-grid">
                <div>
                  <h4>Overview</h4>
                  <p>Designed a body-powered prosthetic hand for print-at-home fabrication, with a four-bar tendon linkage per finger and a wrist-driven actuation cable. Iterated the design through five prototype rounds with a fitting volunteer.</p>
                  <h4>Outcome</h4>
                  <ul class="result-list">
                    <li>Bill of materials cost under $35 per unit</li>
                    <li>Design published for open fabrication by other makers</li>
                  </ul>
                </div>
                <div>
                  <h4>Tools & process</h4>
                  <div class="taglist">
                    <span class="tag">Fusion 360</span><span class="tag">FDM Printing</span><span class="tag">User testing</span>
                  </div>
                </div>
              </div>
            </td>
          </tr>

          <tr class="bom-row" data-target="p4">
            <td class="item">004</td>
            <td class="name">Battery pack thermal management<span class="sub">Cold-plate cooling for a 5 kWh pack</span></td>
            <td class="mat">Cu / Al</td>
            <td class="qty">Thermal</td>
            <td class="chevron">▾</td>
          </tr>
          <tr class="bom-detail" id="p4">
            <td colspan="5">
              <div class="detail-grid">
                <div>
                  <h4>Overview</h4>
                  <p>Ran CFD-driven thermal analysis on a liquid cold-plate design for a lithium-ion battery pack, iterating channel geometry to hold cell-to-cell temperature delta under 3°C at peak discharge.</p>
                  <h4>Outcome</h4>
                  <ul class="result-list">
                    <li>Reduced peak cell temperature by 14°C versus the baseline design</li>
                    <li>Validated the model against thermocouple data on a physical build</li>
                  </ul>
                </div>
                <div>
                  <h4>Tools & process</h4>
                  <div class="taglist">
                    <span class="tag">ANSYS Fluent</span><span class="tag">SolidWorks</span><span class="tag">Test rig build</span>
                  </div>
                </div>
              </div>
            </td>
          </tr>
        </tbody>
      </table>
    </section>

    <!-- ============ SKILLS ============ -->
    <section id="skills" data-sheet="04 / 06">
      <p class="eyebrow">03 — Skills</p>
      <div class="skills-grid">
        <div class="skill-group">
          <h3>Design & CAD</h3>
          <div class="skill-chip-row">
            <span class="chip">SolidWorks</span><span class="chip">Fusion 360</span><span class="chip">AutoCAD</span><span class="chip">Onshape</span>
          </div>
        </div>
        <div class="skill-group">
          <h3>Analysis</h3>
          <div class="skill-chip-row">
            <span class="chip">FEA (ANSYS)</span><span class="chip">CFD</span><span class="chip">MATLAB</span><span class="chip">Thermal modeling</span>
          </div>
        </div>
        <div class="skill-group">
          <h3>Manufacturing</h3>
          <div class="skill-chip-row">
            <span class="chip">CNC machining</span><span class="chip">FDM / SLA printing</span><span class="chip">Sheet metal</span><span class="chip">Welding</span>
          </div>
        </div>
        <div class="skill-group">
          <h3>Process</h3>
          <div class="skill-chip-row">
            <span class="chip">GD&T</span><span class="chip">DFM / DFA</span><span class="chip">Python</span><span class="chip">PLM / PDM</span>
          </div>
        </div>
      </div>
    </section>

    <!-- ============ EXPERIENCE ============ -->
    <section id="experience" data-sheet="05 / 06">
      <p class="eyebrow">04 — Experience</p>
      <div class="timeline">
        <!-- EDIT: your work history, most recent first -->
        <div class="tl-item">
          <div class="tl-date">2023 — Present</div>
          <div class="tl-role">Mechanical Engineer II</div>
          <div class="tl-org">Northline Robotics</div>
          <p class="tl-desc">Own end-effector and actuation design for a warehouse picking robot, from concept CAD through FEA validation and pilot-line manufacturing support.</p>
        </div>
        <div class="tl-item">
          <div class="tl-date">2021 — 2023</div>
          <div class="tl-role">Mechanical Design Engineer</div>
          <div class="tl-org">Ferrous & Co.</div>
          <p class="tl-desc">Designed sheet-metal enclosures and thermal solutions for industrial equipment; led DFM reviews with contract manufacturers.</p>
        </div>
        <div class="tl-item">
          <div class="tl-date">2020 — 2021</div>
          <div class="tl-role">Mechanical Engineering Intern</div>
          <div class="tl-org">Coriolis Labs</div>
          <p class="tl-desc">Built and instrumented test rigs for pump performance validation; automated data reduction in Python.</p>
        </div>
      </div>
    </section>

    <!-- ============ CONTACT ============ -->
    <section id="contact" data-sheet="06 / 06">
      <p class="eyebrow">05 — Contact</p>
      <div class="contact-block">
        <!-- EDIT: closing line -->
        <h2>Building something mechanical? Let's talk.</h2>
        <div class="contact-links">
          <!-- EDIT: your real links -->
          <a href="mailto:jordan.reyes@example.com">jordan.reyes@example.com</a>
          <a href="https://linkedin.com/in/your-handle" target="_blank" rel="noopener">linkedin.com/in/your-handle</a>
          <a href="https://github.com/your-handle" target="_blank" rel="noopener">github.com/your-handle</a>
        </div>
      </div>
    </section>

  </div>
</main>

<footer class="foot">
  <span>© 2026 Marcus Ziniti — Mechanical Engineering Portfolio</span>
  <span>Built with <a href="#hero">↑ Back to top</a></span>
</footer>

<script>
  // Expand / collapse BOM detail rows
  document.querySelectorAll('.bom-row').forEach(function(row){
    row.addEventListener('click', function(){
      var target = document.getElementById(row.dataset.target);
      var isOpen = target.classList.contains('open');
      document.querySelectorAll('.bom-detail.open').forEach(function(d){ d.classList.remove('open'); });
      document.querySelectorAll('.bom-row.open').forEach(function(r){ r.classList.remove('open'); });
      if(!isOpen){
        target.classList.add('open');
        row.classList.add('open');
      }
    });
  });

  // Update the title-block "SHEET" number as the user scrolls between sections
  var sheetEl = document.getElementById('sheet-no');
  var sections = document.querySelectorAll('section[data-sheet]');
  if('IntersectionObserver' in window){
    var obs = new IntersectionObserver(function(entries){
      entries.forEach(function(entry){
        if(entry.isIntersecting){ sheetEl.textContent = entry.target.dataset.sheet; }
      });
    }, { rootMargin: '-45% 0px -45% 0px' });
    sections.forEach(function(s){ obs.observe(s); });
  }
</script>

</body>
</html>
