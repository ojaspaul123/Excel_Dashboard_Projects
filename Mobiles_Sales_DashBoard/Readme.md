<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Mobile Sales Dashboard — Project README</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:ital,wght@0,300;0,400;0,500;1,300&display=swap" rel="stylesheet"/>
<style>
  :root {
    --navy: #0d1b2a;
    --deep: #112240;
    --teal: #0a9396;
    --teal-light: #94d2bd;
    --gold: #e9c46a;
    --white: #f0f4f8;
    --muted: #8892a4;
    --card: #172a45;
    --border: #1e3a5f;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--navy);
    color: var(--white);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    overflow-x: hidden;
  }

  /* ── HERO ── */
  .hero {
    position: relative;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    padding: 80px 10vw;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse 80% 60% at 80% 40%, rgba(10,147,150,0.15) 0%, transparent 60%),
      radial-gradient(ellipse 50% 40% at 20% 80%, rgba(233,196,106,0.08) 0%, transparent 50%);
    pointer-events: none;
  }

  .hero-tag {
    font-family: 'DM Sans', sans-serif;
    font-size: 11px;
    letter-spacing: 3px;
    text-transform: uppercase;
    color: var(--teal);
    border: 1px solid var(--teal);
    padding: 5px 14px;
    border-radius: 20px;
    margin-bottom: 28px;
    display: inline-block;
    animation: fadeUp 0.6s ease forwards;
    opacity: 0;
  }

  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(42px, 7vw, 88px);
    font-weight: 800;
    line-height: 1.0;
    letter-spacing: -2px;
    max-width: 700px;
    animation: fadeUp 0.7s 0.1s ease forwards;
    opacity: 0;
  }

  .hero h1 span { color: var(--teal); }

  .hero-sub {
    margin-top: 24px;
    font-size: 18px;
    color: var(--muted);
    max-width: 480px;
    line-height: 1.7;
    animation: fadeUp 0.7s 0.2s ease forwards;
    opacity: 0;
  }

  .hero-meta {
    margin-top: 40px;
    display: flex;
    gap: 32px;
    flex-wrap: wrap;
    animation: fadeUp 0.7s 0.3s ease forwards;
    opacity: 0;
  }

  .hero-meta-item {
    display: flex;
    align-items: center;
    gap: 8px;
    font-size: 13px;
    color: var(--muted);
    font-weight: 400;
  }

  .hero-meta-item .dot {
    width: 8px; height: 8px;
    border-radius: 50%;
    background: var(--teal);
    flex-shrink: 0;
  }

  .hero-scroll {
    position: absolute;
    bottom: 40px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    color: var(--muted);
    font-size: 11px;
    letter-spacing: 2px;
    text-transform: uppercase;
    animation: fadeUp 0.7s 0.5s ease forwards;
    opacity: 0;
  }

  .scroll-line {
    width: 1px;
    height: 40px;
    background: linear-gradient(to bottom, var(--teal), transparent);
    animation: scrollPulse 2s infinite;
  }

  /* ── KPI STRIP ── */
  .kpi-strip {
    padding: 60px 10vw;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 2px;
    background: var(--border);
  }

  .kpi-card {
    background: var(--card);
    padding: 36px 28px;
    position: relative;
    overflow: hidden;
    opacity: 0;
    transform: translateY(20px);
    transition: all 0.5s ease;
  }

  .kpi-card.visible { opacity: 1; transform: translateY(0); }

  .kpi-card::after {
    content: '';
    position: absolute;
    top: 0; left: 0;
    width: 3px; height: 100%;
    background: var(--teal);
    transform: scaleY(0);
    transform-origin: bottom;
    transition: transform 0.4s ease;
  }

  .kpi-card:hover::after { transform: scaleY(1); }

  .kpi-value {
    font-family: 'Syne', sans-serif;
    font-size: 42px;
    font-weight: 800;
    color: var(--white);
    line-height: 1;
  }

  .kpi-value span { color: var(--teal); }

  .kpi-label {
    margin-top: 8px;
    font-size: 12px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--muted);
  }

  /* ── SECTION ── */
  .section {
    padding: 100px 10vw;
  }

  .section-header {
    margin-bottom: 56px;
    display: flex;
    align-items: baseline;
    gap: 20px;
  }

  .section-num {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    color: var(--teal);
    letter-spacing: 2px;
  }

  .section-title {
    font-family: 'Syne', sans-serif;
    font-size: clamp(28px, 4vw, 44px);
    font-weight: 700;
    letter-spacing: -1px;
  }

  /* ── DASHBOARD VIEWER ── */
  .dashboard-viewer {
    background: var(--deep);
    border: 1px solid var(--border);
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 40px 80px rgba(0,0,0,0.4);
  }

  .viewer-tabs {
    display: flex;
    gap: 0;
    background: var(--navy);
    border-bottom: 1px solid var(--border);
    padding: 0 20px;
  }

  .viewer-tab {
    padding: 14px 24px;
    font-size: 12px;
    letter-spacing: 1px;
    text-transform: uppercase;
    cursor: pointer;
    color: var(--muted);
    border-bottom: 2px solid transparent;
    transition: all 0.2s;
    font-family: 'DM Sans', sans-serif;
    font-weight: 500;
    background: none;
    border-left: none;
    border-right: none;
    border-top: none;
  }

  .viewer-tab.active {
    color: var(--teal);
    border-bottom: 2px solid var(--teal);
  }

  .viewer-tab:hover { color: var(--white); }

  .viewer-panel { display: none; }
  .viewer-panel.active { display: block; }

  .viewer-panel img {
    width: 100%;
    display: block;
  }

  .viewer-caption {
    padding: 20px 28px;
    background: var(--navy);
    font-size: 13px;
    color: var(--muted);
    border-top: 1px solid var(--border);
    line-height: 1.6;
  }

  .viewer-caption strong { color: var(--teal-light); }

  /* ── FEATURES GRID ── */
  .features-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2px;
    background: var(--border);
  }

  .feature-card {
    background: var(--card);
    padding: 40px 32px;
    opacity: 0;
    transform: translateY(30px);
    transition: all 0.5s ease;
  }

  .feature-card.visible { opacity: 1; transform: translateY(0); }
  .feature-card:hover { background: #1d3557; }

  .feature-icon {
    font-size: 28px;
    margin-bottom: 20px;
    display: block;
  }

  .feature-name {
    font-family: 'Syne', sans-serif;
    font-size: 18px;
    font-weight: 700;
    margin-bottom: 12px;
    color: var(--white);
  }

  .feature-desc {
    font-size: 14px;
    color: var(--muted);
    line-height: 1.7;
  }

  /* ── TECH STACK ── */
  .tech-stack {
    display: flex;
    flex-wrap: wrap;
    gap: 12px;
    margin-top: 20px;
  }

  .tech-pill {
    background: transparent;
    border: 1px solid var(--border);
    color: var(--teal-light);
    padding: 8px 18px;
    border-radius: 30px;
    font-size: 13px;
    font-weight: 500;
    letter-spacing: 0.5px;
    transition: all 0.2s;
    cursor: default;
  }

  .tech-pill:hover {
    background: rgba(10,147,150,0.1);
    border-color: var(--teal);
  }

  /* ── DATA INSIGHTS ── */
  .insights-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2px;
    background: var(--border);
    margin-top: 48px;
  }

  .insight-card {
    background: var(--card);
    padding: 36px 32px;
  }

  .insight-title {
    font-family: 'Syne', sans-serif;
    font-size: 14px;
    letter-spacing: 2px;
    text-transform: uppercase;
    color: var(--teal);
    margin-bottom: 20px;
  }

  .insight-list { list-style: none; }

  .insight-list li {
    padding: 10px 0;
    font-size: 14px;
    color: var(--muted);
    border-bottom: 1px solid rgba(255,255,255,0.05);
    display: flex;
    justify-content: space-between;
    align-items: center;
    line-height: 1.5;
  }

  .insight-list li:last-child { border-bottom: none; }

  .insight-list li strong {
    color: var(--white);
    font-weight: 500;
    text-align: right;
    font-size: 13px;
  }

  /* ── BAR CHART VISUAL ── */
  .bar-chart {
    margin-top: 12px;
  }

  .bar-row {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 12px;
  }

  .bar-label {
    font-size: 12px;
    color: var(--muted);
    width: 80px;
    flex-shrink: 0;
    text-align: right;
  }

  .bar-track {
    flex: 1;
    height: 28px;
    background: rgba(255,255,255,0.04);
    border-radius: 2px;
    overflow: hidden;
    position: relative;
  }

  .bar-fill {
    height: 100%;
    border-radius: 2px;
    background: linear-gradient(90deg, var(--teal), var(--teal-light));
    width: 0%;
    transition: width 1.2s cubic-bezier(0.16, 1, 0.3, 1);
    display: flex;
    align-items: center;
    justify-content: flex-end;
    padding-right: 10px;
  }

  .bar-fill.animated { }

  .bar-val {
    font-size: 11px;
    color: var(--navy);
    font-weight: 600;
  }

  /* ── FOOTER ── */
  .footer {
    padding: 60px 10vw;
    border-top: 1px solid var(--border);
    display: flex;
    justify-content: space-between;
    align-items: center;
    flex-wrap: gap;
  }

  .footer-name {
    font-family: 'Syne', sans-serif;
    font-size: 22px;
    font-weight: 700;
  }

  .footer-name span { color: var(--teal); }

  .footer-links {
    display: flex;
    gap: 24px;
  }

  .footer-link {
    font-size: 13px;
    color: var(--muted);
    text-decoration: none;
    transition: color 0.2s;
    letter-spacing: 0.5px;
  }

  .footer-link:hover { color: var(--teal); }

  /* ── DIVIDER ── */
  .divider {
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--teal), transparent);
    margin: 0 10vw;
    opacity: 0.4;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(24px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @keyframes scrollPulse {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.3; }
  }

  @media (max-width: 900px) {
    .kpi-strip { grid-template-columns: 1fr 1fr; }
    .features-grid { grid-template-columns: 1fr 1fr; }
    .insights-grid { grid-template-columns: 1fr; }
  }

  @media (max-width: 600px) {
    .kpi-strip { grid-template-columns: 1fr; }
    .features-grid { grid-template-columns: 1fr; }
    .hero { padding: 60px 6vw; }
    .section { padding: 60px 6vw; }
  }
</style>
</head>
<body>

<!-- ── HERO ── -->
<section class="hero">
  <span class="hero-tag">Power BI · SQL · Data Analytics</span>
  <h1>Mobile Sales<br/><span>Dashboard</span></h1>
  <p class="hero-sub">An end-to-end interactive analytics solution tracking mobile sales across cities, models, and time — built with Power BI and real-world data.</p>
  <div class="hero-meta">
    <div class="hero-meta-item"><span class="dot"></span> Ojas Paul</div>
    <div class="hero-meta-item"><span class="dot"></span> January 2026</div>
    <div class="hero-meta-item"><span class="dot"></span> 3 Dashboard Pages</div>
    <div class="hero-meta-item"><span class="dot"></span> 769M Total Sales</div>
  </div>
  <div class="hero-scroll">
    <div class="scroll-line"></div>
    scroll
  </div>
</section>

<!-- ── KPI STRIP ── -->
<div class="kpi-strip" id="kpiStrip">
  <div class="kpi-card">
    <div class="kpi-value">769<span>M</span></div>
    <div class="kpi-label">Total Sales</div>
  </div>
  <div class="kpi-card">
    <div class="kpi-value">19<span>K</span></div>
    <div class="kpi-label">Total Quantity</div>
  </div>
  <div class="kpi-card">
    <div class="kpi-value">4<span>K</span></div>
    <div class="kpi-label">Transactions</div>
  </div>
  <div class="kpi-card">
    <div class="kpi-value">40<span>.1K</span></div>
    <div class="kpi-label">Avg. Price</div>
  </div>
</div>

<div class="divider" style="margin-top:0;"></div>

<!-- ── DASHBOARD SCREENSHOTS ── -->
<section class="section">
  <div class="section-header">
    <span class="section-num">01</span>
    <h2 class="section-title">Dashboard Pages</h2>
  </div>
  <div class="dashboard-viewer">
    <div class="viewer-tabs">
      <button class="viewer-tab active" onclick="switchTab(0)">Main Dashboard</button>
      <button class="viewer-tab" onclick="switchTab(1)">MTD · QTD · YTD</button>
      <button class="viewer-tab" onclick="switchTab(2)">Same Period Last Year</button>
    </div>
    <div class="viewer-panel active" id="panel-0">
      <img src="DashBoard.png" alt="Main Dashboard"/>
      <div class="viewer-caption">
        <strong>Main Dashboard</strong> — Overview of total sales by city (map), quantity trends by month (line chart), transaction breakdown by payment method (pie), top-performing mobile models, and weekday sales distribution. Features slicers for Mobile Model, Payment Method, and Brand.
      </div>
    </div>
    <div class="viewer-panel" id="panel-1">
      <img src="Slide-II.png" alt="MTD QTD YTD Dashboard"/>
      <div class="viewer-caption">
        <strong>MTD · QTD · YTD Report</strong> — Time-intelligence analysis using DAX measures. MTD (Month-to-Date) report tracks monthly rolling performance; QTD and YTD line charts reveal growth trajectories from 2021 to 2024, showing peak performance in 2022–2023 and slight moderation in 2024.
      </div>
    </div>
    <div class="viewer-panel" id="panel-2">
      <img src="Slide-III.png" alt="Same Period Last Year"/>
      <div class="viewer-caption">
        <strong>Same Period Last Year</strong> — Year-over-year comparison across Year, Quarter, and Month views. Side-by-side bar charts clearly visualize current vs. prior year performance, enabling quick identification of growth and decline periods.
      </div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ── FEATURES ── -->
<section class="section">
  <div class="section-header">
    <span class="section-num">02</span>
    <h2 class="section-title">Key Features</h2>
  </div>
  <div class="features-grid" id="featuresGrid">
    <div class="feature-card">
      <span class="feature-icon">🗺️</span>
      <div class="feature-name">Geo Sales Map</div>
      <div class="feature-desc">Interactive Bing map visualizing Total Sales by City across India — from Ludhiana to Madurai — with bubble sizing by revenue volume.</div>
    </div>
    <div class="feature-card">
      <span class="feature-icon">📅</span>
      <div class="feature-name">Time Intelligence</div>
      <div class="feature-desc">DAX-powered MTD, QTD, and YTD calculations with dynamic slicers for Month, Year, Mobile Model, and Payment Method.</div>
    </div>
    <div class="feature-card">
      <span class="feature-icon">📊</span>
      <div class="feature-name">YoY Comparison</div>
      <div class="feature-desc">Side-by-side current vs. same period last year analysis at Year, Quarter, and Month granularity using time-intelligence DAX measures.</div>
    </div>
    <div class="feature-card">
      <span class="feature-icon">💳</span>
      <div class="feature-name">Payment Analytics</div>
      <div class="feature-desc">Transaction distribution across UPI (26.36%), Credit Card (24.72%), Debit Card (24.69%), and other payment methods via donut chart.</div>
    </div>
    <div class="feature-card">
      <span class="feature-icon">⭐</span>
      <div class="feature-name">Rating Analysis</div>
      <div class="feature-desc">Customer rating segmentation (Good / Average / Poor) with percentage breakdowns, showing strong skew toward positive reviews.</div>
    </div>
    <div class="feature-card">
      <span class="feature-icon">📱</span>
      <div class="feature-name">Model Performance</div>
      <div class="feature-desc">Top mobile models ranked by revenue — iPhone SE (60M), OnePlus Nord (58M), Samsung Galaxy Note (56M), Vivo Y51 (55M).</div>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ── DATA INSIGHTS ── -->
<section class="section">
  <div class="section-header">
    <span class="section-num">03</span>
    <h2 class="section-title">Data Insights</h2>
  </div>

  <div class="insights-grid">
    <div class="insight-card">
      <div class="insight-title">Top Models by Revenue</div>
      <div class="bar-chart" id="barChart">
        <div class="bar-row"><div class="bar-label">iPhone SE</div><div class="bar-track"><div class="bar-fill" data-width="100"><span class="bar-val">60M</span></div></div></div>
        <div class="bar-row"><div class="bar-label">OnePlus Nord</div><div class="bar-track"><div class="bar-fill" data-width="96"><span class="bar-val">58M</span></div></div></div>
        <div class="bar-row"><div class="bar-label">Galaxy Note</div><div class="bar-track"><div class="bar-fill" data-width="93"><span class="bar-val">56M</span></div></div></div>
        <div class="bar-row"><div class="bar-label">Vivo Y51</div><div class="bar-track"><div class="bar-fill" data-width="91"><span class="bar-val">55M</span></div></div></div>
      </div>
    </div>

    <div class="insight-card">
      <div class="insight-title">Payment Method Split</div>
      <ul class="insight-list">
        <li>UPI <strong>26.36%</strong></li>
        <li>Credit Card <strong>24.72%</strong></li>
        <li>Debit Card <strong>24.69%</strong></li>
        <li>Other Methods <strong>24.22%</strong></li>
      </ul>
    </div>

    <div class="insight-card">
      <div class="insight-title">Sales by Day of Week</div>
      <ul class="insight-list">
        <li>Saturday <strong>43.5M</strong></li>
        <li>Monday <strong>42.3M</strong></li>
        <li>Tuesday <strong>42.1M</strong></li>
        <li>Thursday <strong>39.2M</strong></li>
        <li>Wednesday <strong>38.9M</strong></li>
        <li>Friday <strong>38.2M</strong></li>
        <li>Sunday <strong>37.4M</strong></li>
      </ul>
    </div>

    <div class="insight-card">
      <div class="insight-title">YoY Sales Growth</div>
      <ul class="insight-list">
        <li>2021 <strong>~59M</strong></li>
        <li>2022 <strong>~262M (+344%)</strong></li>
        <li>2023 <strong>~253M (−3.4%)</strong></li>
        <li>2024 <strong>~195M (−23%)</strong></li>
      </ul>
    </div>
  </div>
</section>

<div class="divider"></div>

<!-- ── TECH STACK ── -->
<section class="section" style="padding-top: 80px; padding-bottom: 80px;">
  <div class="section-header">
    <span class="section-num">04</span>
    <h2 class="section-title">Tech Stack</h2>
  </div>
  <div class="tech-stack">
    <span class="tech-pill">Power BI Desktop</span>
    <span class="tech-pill">DAX</span>
    <span class="tech-pill">Microsoft Excel (.xlsx)</span>
    <span class="tech-pill">SQL</span>
    <span class="tech-pill">Bing Maps Visual</span>
    <span class="tech-pill">Time-Intelligence Functions</span>
    <span class="tech-pill">Donut / Bar / Line Charts</span>
    <span class="tech-pill">Power Query</span>
    <span class="tech-pill">Interactive Slicers</span>
  </div>
</section>

<!-- ── FOOTER ── -->
<footer class="footer">
  <div>
    <div class="footer-name">Ojas <span>Paul</span></div>
    <div style="font-size:13px; color:var(--muted); margin-top:6px;">Data Analyst · KIIT University, Bhubaneswar</div>
  </div>
  <div class="footer-links">
    <a class="footer-link" href="mailto:ojaspaul123@gmail.com">ojaspaul123@gmail.com</a>
    <a class="footer-link" href="https://www.linkedin.com/in/ojas-paul-324aa5337/">LinkedIn</a>
  </div>
</footer>

<script>
  // Tab switching
  function switchTab(idx) {
    document.querySelectorAll('.viewer-tab').forEach((t, i) => t.classList.toggle('active', i === idx));
    document.querySelectorAll('.viewer-panel').forEach((p, i) => p.classList.toggle('active', i === idx));
  }

  // Intersection observer for animations
  const obs = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.classList.add('visible');
        // Animate bars
        e.target.querySelectorAll('.bar-fill[data-width]').forEach(bar => {
          setTimeout(() => { bar.style.width = bar.dataset.width + '%'; }, 200);
        });
      }
    });
  }, { threshold: 0.1 });

  document.querySelectorAll('.kpi-card, .feature-card').forEach(el => obs.observe(el));

  // Animate bars when section is visible
  const barObs = new IntersectionObserver((entries) => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        e.target.querySelectorAll('.bar-fill[data-width]').forEach((bar, i) => {
          setTimeout(() => { bar.style.width = bar.dataset.width + '%'; }, 200 + i * 100);
        });
        barObs.unobserve(e.target);
      }
    });
  }, { threshold: 0.3 });

  const bc = document.getElementById('barChart');
  if (bc) barObs.observe(bc);
</script>
</body>
</html>
