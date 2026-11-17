# axeon3.io

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LUNA-X — Team Axe Exhibition Hub (axeon3/axeon3.io)</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    .chart-container {
      position: relative;
      width: 100%;
      max-width: 600px;
      margin-left: auto;
      margin-right: auto;
      height: 290px;
      max-height: 360px;
    }
    @media (min-width: 768px) {
      .chart-container {
        height: 330px;
      }
    }
  </style>
</head>
<body class="bg-stone-50 text-slate-800 antialiased selection:bg-amber-100 selection:text-amber-900">
  <!-- Chosen Palette: Warm Stone & Slate Harmony (stone-50 background, white/stone-100 surfaces, slate-800 typography, subtle amber-700 and teal-700 accents) -->
  <!-- Application Structure Plan: Designed a four-zone interactive exhibition hub: (1) Executive Mission Header & KPI Strip summarizing Team Axe's 2026 NASA Space Apps Challenge delivery; (2) Interactive CLPS Hardware Protection Gate & Site Telemetry Simulator allowing users to explore how NASA LOLA/Diviner/SPICE data drives GO/MARGINAL/NO-GO evaluations across candidate sites and CLPS task orders; (3) Filterable Accomplished Tasks Matrix organized across Team Axe's 5 engineering domains (Coordination/Architecture, NASA Science, Frontend/3D UX, DevSecOps/NASA-STD-8739.8B Assurance, and Deliverables); and (4) End-to-End Pipeline Architecture & Post-Submission Milestone Tracker. This structure prioritizes active exploration of how the engineering tasks connect to mission hardware survival rather than passive reading. -->
  <!-- Visualization & Content Choices:
       1. Hardware Gate & Candidate Site Comparison -> Goal: Compare & Inform -> Interactive Radar/Bar Chart (Chart.js Canvas) comparing candidate south-polar sites (Shackleton Site04, Connecting Ridge, Malapert Massif, Nobile Rim) against CLPS survival thresholds (Slope <=10 deg, Solar >=70%, DTE >=55%, PSR <=2.0 km) -> Dropdown & Task-Order Selector -> Lets users test real mission constraints -> Chart.js (Canvas, no SVG).
       2. Accomplished Tasks Explorer -> Goal: Organize & Explore -> Interactive Domain Filter Pills + Search + Expandable Task Cards -> Click filters to isolate axeon3 coordination, NASA modeling, UX, DevSecOps, or deliverables -> Makes 20+ technical milestones easily scannable -> Vanilla JS + Tailwind HTML.
       3. Pipeline & Data Flow Diagram -> Goal: Organize & Explain -> Interactive 5-Stage HTML/CSS Stepper -> Click any pipeline stage to inspect scripts, NASA/Google data sources, and JSON outputs -> Replaces static tables with guided architectural discovery -> HTML/CSS/JS (no SVG/Mermaid).
       4. Milestone Timeline -> Goal: Change & Inform -> Interactive Status Tracker -> Highlights completed Nov 14-15 hackathon submission vs upcoming judging/finalist dates -> HTML/CSS/JS. -->
  <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->

  <header class="bg-white border-b border-stone-200 sticky top-0 z-30">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex flex-col md:flex-row md:items-center md:justify-between gap-3">
      <div>
        <div class="flex items-center gap-2 flex-wrap">
          <span class="px-2.5 py-0.5 text-xs font-semibold tracking-wide uppercase bg-amber-100 text-amber-900 rounded-full">2026 NASA Space Apps · San José</span>
          <span class="px-2.5 py-0.5 text-xs font-mono bg-stone-100 text-slate-700 border border-stone-200 rounded">axeon3/axeon3.io</span>
          <span class="px-2.5 py-0.5 text-xs font-mono bg-stone-100 text-slate-700 border border-stone-200 rounded">upstream: teamaxe/lunar</span>
        </div>
        <h1 class="text-2xl sm:text-3xl font-bold text-slate-900 mt-1 tracking-tight">LUNA-X — Team Axe Exhibition Hub</h1>
        <p class="text-sm text-slate-600">CLPS Lunar Landing Site &amp; Hardware Protection Engine · Powered by NASA Datasets &amp; Google Cloud/AI</p>
      </div>
      <nav class="flex flex-wrap gap-2 text-sm font-medium" aria-label="Primary Navigation">
        <a href="#overview" class="px-3 py-1.5 rounded-lg bg-stone-100 hover:bg-stone-200 text-slate-800 transition">Overview</a>
        <a href="#gates-sim" class="px-3 py-1.5 rounded-lg bg-stone-100 hover:bg-stone-200 text-slate-800 transition">Protection Gates</a>
        <a href="#tasks" class="px-3 py-1.5 rounded-lg bg-stone-100 hover:bg-stone-200 text-slate-800 transition">Accomplished Tasks</a>
        <a href="#pipeline" class="px-3 py-1.5 rounded-lg bg-stone-100 hover:bg-stone-200 text-slate-800 transition">Pipeline &amp; Milestones</a>
      </nav>
    </div>
  </header>

  <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 space-y-12">

    <section id="overview" class="space-y-6">
      <div class="bg-white border border-stone-200 rounded-2xl p-6 sm:p-8 shadow-sm">
        <div class="max-w-4xl space-y-3">
          <h2 class="text-xl font-bold text-slate-900">Mission Context &amp; Exhibition Scope</h2>
          <p class="text-slate-600 leading-relaxed">
            <strong>LUNA-X</strong> (originally <em>LunaScope</em>) is an end-to-end lunar landing site analysis, telemetry synthesis, and hardware protection engine engineered by <strong>Team Axe</strong> (handle: <code class="text-xs bg-stone-100 px-1.5 py-0.5 rounded border border-stone-200">axeone</code>; coordination &amp; architecture lead: <code class="text-xs bg-stone-100 px-1.5 py-0.5 rounded border border-stone-200">axeon3</code>) for the <strong>2026 NASA Space Apps Challenge</strong> (Challenge #10: <em>Lunar Landing Site Navigator</em>, San José local event at SJSU). Built exclusively on authoritative <strong>NASA</strong> lunar datasets and <strong>Google</strong> cloud and AI infrastructure, LUNA-X evaluates south-polar candidate landing zones against strict <strong>Commercial Lunar Payload Services (CLPS)</strong> hardware survival thresholds.
          </p>
        </div>

        <div class="grid grid-cols-2 lg:grid-cols-4 gap-4 mt-6 pt-6 border-t border-stone-200">
          <div class="bg-stone-50 border border-stone-200 rounded-xl p-4">
            <div class="text-xs font-semibold uppercase tracking-wider text-slate-500">CLPS Task Orders</div>
            <div class="text-2xl font-bold text-slate-900 mt-1">6 Profiles</div>
            <div class="text-xs text-slate-600 mt-1">Peregrine, IM-1, Blue Ghost, IM-2, FLIP, Griffin</div>
          </div>
          <div class="bg-stone-50 border border-stone-200 rounded-xl p-4">
            <div class="text-xs font-semibold uppercase tracking-wider text-slate-500">Geodetic Alignment</div>
            <div class="text-2xl font-bold text-teal-800 mt-1">~870 m</div>
            <div class="text-xs text-slate-600 mt-1">MOON_PA (DE421) to MOON_ME frame reconciliation</div>
          </div>
          <div class="bg-stone-50 border border-stone-200 rounded-xl p-4">
            <div class="text-xs font-semibold uppercase tracking-wider text-slate-500">Assurance Standard</div>
            <div class="text-2xl font-bold text-amber-800 mt-1">NASA-STD-8739.8B</div>
            <div class="text-xs text-slate-600 mt-1">CodeQL, Gitleaks v3, Trivy &amp; Syft SBOM CI/CD</div>
          </div>
          <div class="bg-stone-50 border border-stone-200 rounded-xl p-4">
            <div class="text-xs font-semibold uppercase tracking-wider text-slate-500">Hackathon Status</div>
            <div class="text-2xl font-bold text-emerald-800 mt-1">Submitted</div>
            <div class="text-xs text-slate-600 mt-1">Nov 15, 2026 · Advancing to Nov 22 Judging</div>
          </div>
        </div>
      </div>
    </section>

    <section id="gates-sim" class="space-y-6">
      <div class="space-y-2">
        <h2 class="text-2xl font-bold text-slate-900">CLPS Hardware Protection Gates &amp; Site Telemetry Explorer</h2>
        <p class="text-slate-600 max-w-4xl">
          This interactive verification panel demonstrates how <code class="text-xs bg-stone-200/70 px-1.5 py-0.5 rounded">clps_verifier.py</code> evaluates candidate south-polar sites using NASA LOLA elevation rasters, 360° horizon masks, LRO Diviner thermal residuals, and JPL Horizons ephemeris windows. Select a landing site and CLPS task order below to inspect live <code class="text-xs bg-stone-200/70 px-1.5 py-0.5 rounded">GO / MARGINAL / NO-GO</code> gate diagnostics.
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
        <div class="lg:col-span-5 bg-white border border-stone-200 rounded-2xl p-6 shadow-sm flex flex-col justify-between space-y-6">
          <div class="space-y-4">
            <div class="flex items-center justify-between">
              <span class="text-xs font-bold uppercase tracking-wider text-slate-500">Telemetry Selector</span>
              <span id="site-verdict-badge" class="px-3 py-1 text-xs font-bold rounded-full bg-emerald-100 text-emerald-900">GO — ALL GATES PASSED</span>
            </div>

            <div class="grid grid-cols-1 sm:grid-cols-2 gap-3">
              <div>
                <label for="site-select" class="block text-xs font-semibold text-slate-700 mb-1">Candidate Lunar Site</label>
                <select id="site-select" class="w-full rounded-lg border border-stone-300 bg-stone-50 px-3 py-2 text-sm text-slate-800 focus:outline-none focus:ring-2 focus:ring-amber-600">
                  <option value="site04">Site04 — Shackleton Rim (Fixture)</option>
                  <option value="ridge">Connecting Ridge — Peak of Light</option>
                  <option value="malapert">Malapert Massif — Plateau</option>
                  <option value="nobile">Nobile Rim — Steep Crater Wall</option>
                </select>
              </div>
              <div>
                <label for="clps-select" class="block text-xs font-semibold text-slate-700 mb-1">CLPS Task Order Profile</label>
                <select id="clps-select" class="w-full rounded-lg border border-stone-300 bg-stone-50 px-3 py-2 text-sm text-slate-800 focus:outline-none focus:ring-2 focus:ring-amber-600">
                  <option value="to20a">to20a — Griffin (VIPER-class)</option>
                  <option value="im-2">im-2 — Athena (Nova-C)</option>
                  <option value="to19d">to19d — Blue Ghost M1</option>
                  <option value="to2-im">to2-im — IM-1 Odysseus</option>
                  <option value="to2-ab">to2-ab — Peregrine</option>
                  <option value="flip-rover">flip-rover — Lunar Rover</option>
                </select>
              </div>
            </div>

            <div id="gate-cards" class="space-y-3 pt-2"></div>
          </div>

          <div id="site-notes" class="bg-stone-50 border border-stone-200 rounded-xl p-4 text-xs text-slate-600 leading-relaxed"></div>
        </div>

        <div class="lg:col-span-7 bg-white border border-stone-200 rounded-2xl p-6 shadow-sm flex flex-col justify-between">
          <div class="mb-4">
            <h3 class="text-base font-bold text-slate-900">Normalized Gate Compliance vs. CLPS Thresholds</h3>
            <p class="text-xs text-slate-500">Values normalized to 100% minimum survival threshold (dashed boundary = 100% gate compliance; higher indicates greater safety margin).</p>
          </div>
          <div class="chart-container">
            <canvas id="gatesChart"></canvas>
          </div>
          <div class="mt-4 pt-3 border-t border-stone-100 flex flex-wrap items-center justify-between gap-2 text-xs text-slate-500">
            <span>Sources: NASA LRO LOLA (LDEM_875S_5M), Diviner Ch. 8/9, NAIF SPICE DE440</span>
            <span id="telemetry-file-tag" class="font-mono bg-stone-100 px-2 py-0.5 rounded text-slate-700">telemetry_site04.json</span>
          </div>
        </div>
      </div>
    </section>

    <section id="tasks" class="space-y-6">
      <div class="flex flex-col md:flex-row md:items-end md:justify-between gap-4">
        <div class="space-y-2 max-w-3xl">
          <h2 class="text-2xl font-bold text-slate-900">Accomplished Tasks — Team Axe</h2>
          <p class="text-slate-600">
            Explore all completed engineering, scientific modeling, frontend UX, software assurance, and hackathon deliverables across Team Axe. Filter by workstream or search specific scripts, NASA datasets, and Google cloud services.
          </p>
        </div>
        <div class="w-full md:w-72">
          <label for="task-search" class="sr-only">Search accomplished tasks</label>
          <input id="task-search" type="text" placeholder="Search scripts, NASA, Google, CI..." class="w-full rounded-xl border border-stone-300 bg-white px-3.5 py-2 text-sm text-slate-800 placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-amber-600" />
        </div>
      </div>

      <div id="domain-filters" class="flex flex-wrap gap-2"></div>

      <div id="tasks-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5"></div>
    </section>

    <section id="pipeline" class="space-y-6">
      <div class="space-y-2 max-w-4xl">
        <h2 class="text-2xl font-bold text-slate-900">End-to-End Pipeline Architecture &amp; Attribution</h2>
        <p class="text-slate-600">
          LUNA-X decouples heavy scientific ingestion and ephemeris calculation from real-time browser visualization via <code class="text-xs bg-stone-200/70 px-1.5 py-0.5 rounded">run_pipeline.sh</code>. Select any stage below to inspect its execution scripts, NASA/Google inputs, and verified artifacts.
        </p>
      </div>

      <div class="bg-white border border-stone-200 rounded-2xl p-6 shadow-sm space-y-6">
        <div id="pipeline-steps" class="grid grid-cols-1 sm:grid-cols-5 gap-3"></div>
        <div id="pipeline-detail" class="bg-stone-50 border border-stone-200 rounded-xl p-5"></div>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-12 gap-6">
        <div class="lg:col-span-6 bg-white border border-stone-200 rounded-2xl p-6 shadow-sm space-y-4">
          <h3 class="text-lg font-bold text-slate-900">Upstream NASA Datasets &amp; Google Infrastructure</h3>
          <p class="text-xs text-slate-500">All scientific rasters, ephemeris kernels, and cloud runtimes used in LUNA-X are strictly attributed below.</p>
          <ul class="space-y-3 text-sm text-slate-700">
            <li class="p-3 rounded-xl bg-stone-50 border border-stone-200">
              <div class="font-semibold text-slate-900">NASA LRO LOLA Topography &amp; Geodesy</div>
              <div class="text-xs text-slate-600 mt-0.5">PDS LOLA <code class="font-mono">LDEM_875S_5M.JP2</code> &amp; PGDA Product 78 (<code class="font-mono">MOON_ME</code> / <code class="font-mono">DE421</code>) — Barker et al. (2021), Mazarico et al. (2011).</div>
            </li>
            <li class="p-3 rounded-xl bg-stone-50 border border-stone-200">
              <div class="font-semibold text-slate-900">NASA LRO Diviner Lunar Radiometer</div>
              <div class="text-xs text-slate-600 mt-0.5">Channel 8/9 and bolometric thermal residual validation — Paige et al. (2010).</div>
            </li>
            <li class="p-3 rounded-xl bg-stone-50 border border-stone-200">
              <div class="font-semibold text-slate-900">NASA/JPL NAIF SPICE &amp; Horizons REST API</div>
              <div class="text-xs text-slate-600 mt-0.5">DE440 planetary ephemeris kernels &amp; live Sun/Earth topocentric azimuth/elevation windows.</div>
            </li>
            <li class="p-3 rounded-xl bg-stone-50 border border-stone-200">
              <div class="font-semibold text-slate-900">Google Cloud, Firebase &amp; Google AI Studio</div>
              <div class="text-xs text-slate-600 mt-0.5">Firebase (<code class="font-mono">luna-x</code> / <code class="font-mono">gen-lang-client-0427491063</code>), Google Cloud Run (<code class="font-mono">us-east1</code>), Google AI Studio, and Google Groups (<code class="font-mono">axeon3@googlegroups.com</code>).</div>
            </li>
          </ul>
        </div>

        <div class="lg:col-span-6 bg-white border border-stone-200 rounded-2xl p-6 shadow-sm space-y-4">
          <h3 class="text-lg font-bold text-slate-900">2026 NASA Space Apps Post-Submission Roadmap</h3>
          <p class="text-xs text-slate-500">Tracking Team Axe's progress from the San José local hackathon through global judging.</p>
          <div class="space-y-3" id="milestones-list"></div>
        </div>
      </div>
    </section>

  </main>

  <footer class="border-t border-stone-200 bg-white mt-12">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-6 flex flex-col sm:flex-row items-center justify-between gap-3 text-xs text-slate-500">
      <div>
        <strong>Team Axe</strong> (<code class="font-mono">axeone</code>) · Dynamic Coordination &amp; Architecture (<code class="font-mono">axeon3</code>) · Apache 2.0 License
      </div>
      <div>
        Built for 2026 NASA Space Apps Challenge · San José, CA
      </div>
    </div>
  </footer>

  <script>
    const SITES = {
      site04: {
        name: "Site04 — Shackleton Rim (Fixture)",
        file: "telemetry_site04.json",
        slopeDeg: 5.4,
        solarPct: 84.2,
        dtePct: 68.5,
        psrKm: 1.15,
        divinerResidualK: 2.1,
        note: "Primary validation fixture (shackleton_site04_fixture.json). High solar illumination duty cycle (84.2%) along the Shackleton rim with 1.15 km traverse radius to sub-40 K Permanently Shadowed Regions and verified LRO Diviner thermal residuals."
      },
      ridge: {
        name: "Connecting Ridge — Peak of Light",
        file: "telemetry_connecting_ridge.json",
        slopeDeg: 6.8,
        solarPct: 89.0,
        dtePct: 72.0,
        psrKm: 1.65,
        divinerResidualK: 2.4,
        note: "Extended illumination ridge between Shackleton and de Gerlache craters. Exceeds all four CLPS survival gates with optimal power generation and Direct-to-Earth visibility."
      },
      malapert: {
        name: "Malapert Massif — Summit Plateau",
        file: "telemetry_malapert.json",
        slopeDeg: 8.6,
        solarPct: 76.4,
        dtePct: 88.0,
        psrKm: 2.45,
        divinerResidualK: 3.0,
        note: "Exceptional Direct-to-Earth line-of-sight (88.0%) due to elevated latitude visibility, but PSR traverse distance (2.45 km) exceeds the 2.0 km rover volatile-access gate (MARGINAL)."
      },
      nobile: {
        name: "Nobile Rim — Steep Crater Wall",
        file: "telemetry_nobile_wall.json",
        slopeDeg: 13.4,
        solarPct: 63.0,
        dtePct: 52.0,
        psrKm: 0.85,
        divinerResidualK: 4.2,
        note: "Close proximity to sub-40 K PSRs (0.85 km), but terrain slope (13.4°) violates the <= 10° lander tip-over gate and horizon masking drops solar duty cycle below 70% (NO-GO)."
      }
    };

    const CLPS_PROFILES = {
      "to20a": { label: "to20a — Griffin", maxSlope: 10.0, minSolar: 70.0, minDte: 55.0, maxPsr: 2.0 },
      "im-2": { label: "im-2 — Athena", maxSlope: 10.0, minSolar: 70.0, minDte: 55.0, maxPsr: 2.0 },
      "to19d": { label: "to19d — Blue Ghost M1", maxSlope: 9.5, minSolar: 72.0, minDte: 55.0, maxPsr: 2.0 },
      "to2-im": { label: "to2-im — IM-1 Odysseus", maxSlope: 10.0, minSolar: 70.0, minDte: 55.0, maxPsr: 2.0 },
      "to2-ab": { label: "to2-ab — Peregrine", maxSlope: 9.0, minSolar: 70.0, minDte: 55.0, maxPsr: 2.0 },
      "flip-rover": { label: "flip-rover — Lunar Rover", maxSlope: 12.0, minSolar: 68.0, minDte: 55.0, maxPsr: 2.5 }
    };

    const ACCOMPLISHED_TASKS = [
      {
        domain: "Coordination & Architecture",
        badge: "axeon3 Lead",
        title: "Decoupled Pipeline Architecture",
        desc: "Designed modular repository layout and run_pipeline.sh orchestrator producing standardized telemetry_<site>.json payloads for frontend consumption.",
        tags: ["run_pipeline.sh", "telemetry_<site>.json", "Architecture"]
      },
      {
        domain: "Coordination & Architecture",
        badge: "axeon3 Lead",
        title: "Coordinate Frame Reconciliation (~870 m)",
        desc: "Implemented frame_align.py to resolve the ~870 m spatial offset between MOON_PA (DE421) and MOON_ME lunar reference frames across NASA rasters.",
        tags: ["frame_align.py", "MOON_PA", "MOON_ME", "DE421"]
      },
      {
        domain: "Coordination & Architecture",
        badge: "axeon3 Lead",
        title: "NASA/JPL SPICE & Horizons Ingestion",
        desc: "Built sync_spice.sh and libration_sim.py using NAIF SPICE DE440 kernels and live JPL Horizons REST API (--live-horizons) for Sun/Earth ephemerides.",
        tags: ["sync_spice.sh", "libration_sim.py", "SPICE DE440", "JPL Horizons"]
      },
      {
        domain: "Coordination & Architecture",
        badge: "axeon3 Lead",
        title: "Six CLPS Task-Order Telemetry Profiles",
        desc: "Modeled lander survival constraints across to2-ab (Peregrine), to2-im (IM-1), to19d (Blue Ghost M1), im-2 (Athena), flip-rover, and to20a (Griffin).",
        tags: ["CLPS", "to20a", "im-2", "to19d", "to2-im"]
      },
      {
        domain: "Coordination & Architecture",
        badge: "axeon3 Lead",
        title: "Automated CLPS Verification Matrix",
        desc: "Engineered clps_verifier.py with a three-tier GO / MARGINAL / NO-GO gate engine, nsac.py, unit tests (test_nsac.py), and shackleton_site04_fixture.json.",
        tags: ["clps_verifier.py", "test_nsac.py", "Site04 Fixture"]
      },
      {
        domain: "Coordination & Architecture",
        badge: "Google Cloud & AI",
        title: "Firebase, Cloud Run & AI Studio Setup",
        desc: "Configured Firebase (luna-x / gen-lang-client-0427491063), us-east1 Google Cloud Run authorized domains, Google AI Studio app integration, and Google Groups.",
        tags: ["Firebase", "Cloud Run us-east1", "Google AI Studio"]
      },
      {
        domain: "NASA Scientific Modeling",
        badge: "Topography",
        title: "NASA LRO LOLA DEM/DTM Ingestion",
        desc: "Automated lunar south-pole elevation raster retrieval via fetch_lola_dem.sh using PDS LOLA LDEM_875S_5M.JP2 and PGDA Product 78.",
        tags: ["fetch_lola_dem.sh", "LDEM_875S_5M.JP2", "PGDA Product 78"]
      },
      {
        domain: "NASA Scientific Modeling",
        badge: "Terrain Masking",
        title: "360° Horizon Masking & Slope Analysis",
        desc: "Built calc_horizon_mask.py to compute terrain tilt angles and full 360-degree horizon_mask_deg topographic obstruction profiles.",
        tags: ["calc_horizon_mask.py", "horizon_mask_deg", "Slope <= 10°"]
      },
      {
        domain: "NASA Scientific Modeling",
        badge: "Cryogenics",
        title: "Cryogenic Thermal & PSR Traverse Modeling",
        desc: "Implemented thermal_model.py to simulate surface cooling curves and measure psr_distance_km to sub-40 K Permanently Shadowed Regions.",
        tags: ["thermal_model.py", "psr_distance_km", "Sub-40 K PSR"]
      },
      {
        domain: "NASA Scientific Modeling",
        badge: "Radiometry",
        title: "NASA LRO Diviner Residual Validation",
        desc: "Developed diviner_validate.py for Channel 8/9 and bolometric thermal residual cross-validation against NASA LRO Diviner observations.",
        tags: ["diviner_validate.py", "LRO Diviner", "Channel 8/9"]
      },
      {
        domain: "Frontend & 3D UX",
        badge: "Web App",
        title: "Dual-Mode Mission Planner & Public Explorer",
        desc: "Delivered index.html and explorer_mode.js in a WCAG-compliant #181825 dark-navy palette supporting technical engineers and public learners.",
        tags: ["index.html", "explorer_mode.js", "WCAG #181825"]
      },
      {
        domain: "Frontend & 3D UX",
        badge: "Visualization",
        title: "Interactive 3D Terrain & Polar Canvas Views",
        desc: "Integrated 3D terrain mesh viewer, polar stereographic canvas map, site selector, dual-ribbon solar/comm timelines, and live status badges.",
        tags: ["3D Terrain", "Polar Canvas", "Dual-Ribbon Timelines"]
      },
      {
        domain: "Frontend & 3D UX",
        badge: "Artemis III",
        title: "Artemis III PSI & Dust Mitigation Addendum",
        desc: "Documented NASA Artemis III Plume-Surface Interaction (PSI) and regolith dust mitigation protocols alongside GitHub Pages deployment.",
        tags: ["Artemis III", "PSI", "Dust Mitigation", "GitHub Pages"]
      },
      {
        domain: "DevSecOps & Assurance",
        badge: "CI/CD",
        title: "Automated Verification & Assurance Workflows",
        desc: "Deployed .github/workflows/clps-verify.yml and cwe-swa-mitre-assurance.yml paired with cwe_swa_mitre_audit.py.",
        tags: ["clps-verify.yml", "cwe_swa_mitre_audit.py", "GitHub Actions"]
      },
      {
        domain: "DevSecOps & Assurance",
        badge: "Security",
        title: "Multi-Language CodeQL, Gitleaks & Trivy",
        desc: "Configured CodeQL (c-cpp, python, javascript-typescript), Gitleaks v3 secret detection, and Trivy container/dependency scanning.",
        tags: ["CodeQL", "Gitleaks v3", "Trivy"]
      },
      {
        domain: "DevSecOps & Assurance",
        badge: "Governance",
        title: "NASA-STD-8739.8B Records & Syft SBOM",
        desc: "Established 90-day NASA-STD-8739.8B software assurance records, Apache 2.0 licensing, Syft SBOM (ATTRIBUTIONS.md), and Contributor Code of Conduct.",
        tags: ["NASA-STD-8739.8B", "Syft SBOM", "Apache 2.0"]
      },
      {
        domain: "Deliverables & Submission",
        badge: "Documentation",
        title: "Technical & Executive Documentation Suite",
        desc: "Authored LUNA-X Documentation (clpsv0ta.docx), Software Architecture & Execution Guide, and Team Axe — Credits & Cited Sources.",
        tags: ["clpsv0ta.docx", "Architecture Guide", "Cited Sources"]
      },
      {
        domain: "Deliverables & Submission",
        badge: "Media & Pitch",
        title: "7-Slide Pitch Deck & Mission Control Audio",
        desc: "Produced the Team Axe — luna-x 7-slide presentation, interactive demo walkthrough, and 30-second ambient audio track (team_axe_lunar_sound.mp3).",
        tags: ["Pitch Deck", "team_axe_lunar_sound.mp3", "Demo"]
      },
      {
        domain: "Deliverables & Submission",
        badge: "Completed",
        title: "2026 NASA Space Apps Global Submission",
        desc: "Completed San José local event at SJSU Student Union Building (Nov 14–15, 2026) and submitted global entry ahead of the Nov 15 11:59 PM PST cutoff.",
        tags: ["SJSU San José", "Nov 15, 2026", "Submitted"]
      }
    ];

    const PIPELINE_STAGES = [
      {
        step: "01",
        title: "Data Acquisition",
        scripts: "fetch_lola_dem.sh · sync_spice.sh",
        summary: "Ingests high-resolution NASA LRO LOLA elevation rasters (LDEM_875S_5M.JP2, PGDA Product 78) and downloads NAIF SPICE DE440 planetary ephemeris kernels.",
        artifacts: "Raw DEM rasters & SPICE binary kernels (.bsp, .tpc, .tls)"
      },
      {
        step: "02",
        title: "Geodesy & Ephemeris",
        scripts: "frame_align.py · libration_sim.py",
        summary: "Reconciles the ~870 m MOON_PA (DE421) to MOON_ME coordinate offset and queries JPL Horizons REST API (--live-horizons) for Sun/Earth azimuth and elevation.",
        artifacts: "Aligned lunar coordinates & topocentric Sun/Earth visibility vectors"
      },
      {
        step: "03",
        title: "Terrain & Thermal",
        scripts: "calc_horizon_mask.py · thermal_model.py · diviner_validate.py",
        summary: "Computes terrain slope, 360° horizon_mask_deg obstruction profiles, cryogenic cooling curves, PSR traverse radius, and LRO Diviner Ch. 8/9 thermal residuals.",
        artifacts: "Horizon masks, PSR proximity (km), and Diviner-validated thermal profiles"
      },
      {
        step: "04",
        title: "Verification & CI",
        scripts: "clps_verifier.py · cwe_swa_mitre_audit.py · run_pipeline.sh",
        summary: "Evaluates candidate sites against CLPS task-order thresholds (GO / MARGINAL / NO-GO) and enforces NASA-STD-8739.8B quality & security checks via GitHub Actions.",
        artifacts: "telemetry_<site>.json payloads & 90-day NASA-STD-8739.8B audit logs"
      },
      {
        step: "05",
        title: "Frontend & Cloud",
        scripts: "index.html · explorer_mode.js · Google Cloud / AI Studio",
        summary: "Renders interactive 3D terrain, polar stereographic canvas maps, and dual-ribbon timelines across Mission Planner and Public Explorer modes on Google Cloud Run & Firebase.",
        artifacts: "Live web application (luna-x) & GitHub exhibition hub (axeon3.io)"
      }
    ];

    const MILESTONES = [
      { date: "Nov 14–15, 2026", title: "San José Local Event & Global Submission Cutoff (11:59 PM PST)", status: "Completed", done: true },
      { date: "Nov 22, 2026", title: "San José Local Judging (SJSU Cohort)", status: "Upcoming", done: false },
      { date: "Nov 30, 2026", title: "Global Participant Survey Close", status: "Upcoming", done: false },
      { date: "Dec 2026", title: "Global Nominees & Finalists Announcement", status: "Upcoming", done: false },
      { date: "Jan 2027", title: "2026 NASA Space Apps Global Winners Announcement", status: "Upcoming", done: false }
    ];

    let gatesChart = null;
    let activeDomain = "All";
    let activeStageIndex = 0;

    function wrapLabel(str, maxLen = 16) {
      if (str.length <= maxLen) return str;
      const words = str.split(" ");
      const lines = [];
      let current = "";
      words.forEach(w => {
        if ((current + " " + w).trim().length <= maxLen) {
          current = (current + " " + w).trim();
        } else {
          if (current) lines.push(current);
          current = w;
        }
      });
      if (current) lines.push(current);
      return lines;
    }

    function evaluateSite(siteKey, profileKey) {
      const s = SITES[siteKey];
      const p = CLPS_PROFILES[profileKey];

      const slopePass = s.slopeDeg <= p.maxSlope;
      const solarPass = s.solarPct >= p.minSolar;
      const dtePass = s.dtePct >= p.minDte;
      const psrPass = s.psrKm <= p.maxPsr;

      const gates = [
        {
          label: "Ground Tilt / Slope",
          actual: `${s.slopeDeg.toFixed(1)}°`,
          threshold: `<= ${p.maxSlope.toFixed(1)}°`,
          pass: slopePass,
          normScore: Math.round((p.maxSlope / s.slopeDeg) * 100)
        },
        {
          label: "Solar Duty Cycle",
          actual: `${s.solarPct.toFixed(1)}%`,
          threshold: `>= ${p.minSolar.toFixed(0)}%`,
          pass: solarPass,
          normScore: Math.round((s.solarPct / p.minSolar) * 100)
        },
        {
          label: "Direct-to-Earth Link",
          actual: `${s.dtePct.toFixed(1)}%`,
          threshold: `>= ${p.minDte.toFixed(0)}%`,
          pass: dtePass,
          normScore: Math.round((s.dtePct / p.minDte) * 100)
        },
        {
          label: "PSR Traverse Radius",
          actual: `${s.psrKm.toFixed(2)} km`,
          threshold: `<= ${p.maxPsr.toFixed(1)} km`,
          pass: psrPass,
          normScore: Math.round((p.maxPsr / s.psrKm) * 100)
        }
      ];

      let status = "GO";
      let badgeClass = "bg-emerald-100 text-emerald-900";
      let statusText = "GO — ALL GATES PASSED";

      if (!slopePass || !solarPass) {
        status = "NO-GO";
        badgeClass = "bg-rose-100 text-rose-900";
        statusText = "NO-GO — CRITICAL SURVIVAL VIOLATION";
      } else if (!dtePass || !psrPass) {
        status = "MARGINAL";
        badgeClass = "bg-amber-100 text-amber-900";
        statusText = "MARGINAL — SECONDARY GATE EXCEEDED";
      }

      const badgeEl = document.getElementById("site-verdict-badge");
      badgeEl.className = `px-3 py-1 text-xs font-bold rounded-full ${badgeClass}`;
      badgeEl.textContent = statusText;

      const cardsEl = document.getElementById("gate-cards");
      cardsEl.innerHTML = gates.map(g => `
        <div class="flex items-center justify-between p-3 rounded-xl border ${g.pass ? "bg-stone-50 border-stone-200" : "bg-rose-50/70 border-rose-200"}">
          <div>
            <div class="text-xs font-bold text-slate-800">${g.label}</div>
            <div class="text-xs text-slate-500">Gate: <code class="font-mono">${g.threshold}</code></div>
          </div>
          <div class="text-right">
            <div class="text-sm font-bold ${g.pass ? "text-slate-900" : "text-rose-800"}">${g.actual}</div>
            <span class="inline-block text-[11px] font-semibold px-2 py-0.5 rounded ${g.pass ? "bg-emerald-100 text-emerald-900" : "bg-rose-100 text-rose-900"}">
              ${g.pass ? "PASS" : "FAIL"} (${g.normScore}%)
            </span>
          </div>
        </div>
      `).join("");

      document.getElementById("site-notes").innerHTML = `
        <strong>Telemetry Note (${p.label}):</strong> ${s.note}
        <span class="block mt-1 font-mono text-[11px] text-slate-500">Diviner Thermal Residual: ${s.divinerResidualK.toFixed(1)} K RMS</span>
      `;
      document.getElementById("telemetry-file-tag").textContent = s.file;

      updateChart(gates, s.name);
    }

    function updateChart(gates, siteName) {
      const ctx = document.getElementById("gatesChart").getContext("2d");
      const labels = gates.map(g => wrapLabel(g.label, 16));
      const scores = gates.map(g => Math.min(g.normScore, 180));
      const thresholdLine = gates.map(() => 100);
      const barColors = gates.map(g => g.pass ? "rgba(15, 118, 110, 0.82)" : "rgba(190, 18, 60, 0.82)");

      if (gatesChart) {
        gatesChart.data.labels = labels;
        gatesChart.data.datasets[0].label = siteName;
        gatesChart.data.datasets[0].data = scores;
        gatesChart.data.datasets[0].backgroundColor = barColors;
        gatesChart.update();
        return;
      }

      gatesChart = new Chart(ctx, {
        type: "bar",
        data: {
          labels,
          datasets: [
            {
              label: siteName,
              data: scores,
              backgroundColor: barColors,
              borderRadius: 6,
              barPercentage: 0.55
            },
            {
              label: "100% Survival Gate Threshold",
              data: thresholdLine,
              type: "line",
              borderColor: "#b45309",
              borderWidth: 2,
              borderDash: [6, 4],
              pointRadius: 3,
              pointBackgroundColor: "#b45309",
              fill: false
            }
          ]
        },
        options: {
          responsive: true,
          maintainAspectRatio: false,
          scales: {
            y: {
              beginAtZero: true,
              max: 180,
              grid: { color: "#e7e5e4" },
              ticks: {
                callback: v => v + "%",
                color: "#475569",
                font: { size: 11 }
              },
              title: {
                display: true,
                text: "Normalized Compliance (%)",
                color: "#475569",
                font: { size: 11, weight: "bold" }
              }
            },
            x: {
              grid: { display: false },
              ticks: { color: "#334155", font: { size: 11 } }
            }
          },
          plugins: {
            legend: {
              position: "bottom",
              labels: { boxWidth: 12, font: { size: 11 }, color: "#334155" }
            },
            tooltip: {
              callbacks: {
                label: ctx => `${ctx.dataset.label}: ${ctx.parsed.y}%`
              }
            }
          }
        }
      });
    }

    function renderDomainFilters() {
      const domains = ["All", ...new Set(ACCOMPLISHED_TASKS.map(t => t.domain))];
      const container = document.getElementById("domain-filters");
      container.innerHTML = domains.map(d => {
        const isActive = d === activeDomain;
        return `
          <button type="button" data-domain="${d}" class="px-3.5 py-1.5 rounded-full text-xs font-semibold transition border ${
            isActive
              ? "bg-slate-900 text-white border-slate-900"
              : "bg-white text-slate-700 border-stone-300 hover:bg-stone-100"
          }">
            ${d}
          </button>
        `;
      }).join("");

      container.querySelectorAll("button").forEach(btn => {
        btn.addEventListener("click", () => {
          activeDomain = btn.getAttribute("data-domain");
          renderDomainFilters();
          renderTasks();
        });
      });
    }

    function renderTasks() {
      const query = document.getElementById("task-search").value.trim().toLowerCase();
      const filtered = ACCOMPLISHED_TASKS.filter(t => {
        const domainMatch = activeDomain === "All" || t.domain === activeDomain;
        const textMatch = !query ||
          t.title.toLowerCase().includes(query) ||
          t.desc.toLowerCase().includes(query) ||
          t.domain.toLowerCase().includes(query) ||
          t.tags.some(tag => tag.toLowerCase().includes(query));
        return domainMatch && textMatch;
      });

      const grid = document.getElementById("tasks-grid");
      if (!filtered.length) {
        grid.innerHTML = `
          <div class="col-span-full bg-white border border-stone-200 rounded-2xl p-8 text-center text-sm text-slate-500">
            No accomplished tasks match your current filter or search term.
          </div>
        `;
        return;
      }

      grid.innerHTML = filtered.map(t => `
        <article class="bg-white border border-stone-200 rounded-2xl p-5 shadow-sm flex flex-col justify-between space-y-4 hover:border-amber-600/50 transition">
          <div class="space-y-2">
            <div class="flex items-center justify-between gap-2">
              <span class="text-[11px] font-bold uppercase tracking-wider text-amber-800">${t.domain}</span>
              <span class="text-[11px] font-medium px-2 py-0.5 rounded bg-stone-100 text-slate-700 border border-stone-200">${t.badge}</span>
            </div>
            <h3 class="text-base font-bold text-slate-900">${t.title}</h3>
            <p class="text-xs text-slate-600 leading-relaxed">${t.desc}</p>
          </div>
          <div class="flex flex-wrap gap-1.5 pt-2 border-t border-stone-100">
            ${t.tags.map(tag => `<span class="text-[11px] font-mono bg-stone-50 text-slate-700 border border-stone-200 px-2 py-0.5 rounded">${tag}</span>`).join("")}
          </div>
        </article>
      `).join("");
    }

    function renderPipeline() {
      const stepsEl = document.getElementById("pipeline-steps");
      stepsEl.innerHTML = PIPELINE_STAGES.map((st, idx) => {
        const active = idx === activeStageIndex;
        return `
          <button type="button" data-idx="${idx}" class="text-left p-4 rounded-xl border transition ${
            active
              ? "bg-slate-900 text-white border-slate-900 shadow-sm"
              : "bg-stone-50 text-slate-800 border-stone-200 hover:bg-stone-100"
          }">
            <div class="text-xs font-mono ${active ? "text-amber-300" : "text-amber-800"} font-bold">STAGE ${st.step}</div>
            <div class="text-sm font-bold mt-1">${st.title}</div>
          </button>
        `;
      }).join("");

      stepsEl.querySelectorAll("button").forEach(btn => {
        btn.addEventListener("click", () => {
          activeStageIndex = Number(btn.getAttribute("data-idx"));
          renderPipeline();
        });
      });

      const current = PIPELINE_STAGES[activeStageIndex];
      document.getElementById("pipeline-detail").innerHTML = `
        <div class="flex flex-col md:flex-row md:items-center md:justify-between gap-2 pb-3 border-b border-stone-200">
          <div>
            <span class="text-xs font-mono font-bold text-amber-800">STAGE ${current.step}</span>
            <h3 class="text-lg font-bold text-slate-900">${current.title}</h3>
          </div>
          <code class="text-xs bg-white border border-stone-200 px-3 py-1 rounded-lg text-slate-800">${current.scripts}</code>
        </div>
        <p class="text-sm text-slate-700 mt-3 leading-relaxed">${current.summary}</p>
        <div class="mt-3 text-xs text-slate-600">
          <strong>Verified Stage Output:</strong> <span class="font-mono text-slate-800">${current.artifacts}</span>
        </div>
      `;
    }

    function renderMilestones() {
      const list = document.getElementById("milestones-list");
      list.innerHTML = MILESTONES.map(m => `
        <div class="flex items-center justify-between gap-3 p-3 rounded-xl border ${m.done ? "bg-emerald-50/60 border-emerald-200" : "bg-stone-50 border-stone-200"}">
          <div>
            <div class="text-xs font-bold text-slate-500">${m.date}</div>
            <div class="text-sm font-semibold text-slate-900">${m.title}</div>
          </div>
          <span class="shrink-0 px-2.5 py-1 rounded-full text-xs font-bold ${m.done ? "bg-emerald-100 text-emerald-900" : "bg-amber-100 text-amber-900"}">
            ${m.status}
          </span>
        </div>
      `).join("");
    }

    document.getElementById("site-select").addEventListener("change", e => {
      evaluateSite(e.target.value, document.getElementById("clps-select").value);
    });
    document.getElementById("clps-select").addEventListener("change", e => {
      evaluateSite(document.getElementById("site-select").value, e.target.value);
    });
    document.getElementById("task-search").addEventListener("input", renderTasks);

    evaluateSite("site04", "to20a");
    renderDomainFilters();
    renderTasks();
    renderPipeline();
    renderMilestones();
  </script>
</body>
</html>
```
