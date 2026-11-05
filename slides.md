---
theme: default
title: 'Linking the Fabric: Persistent Identifiers and the geoconnex Knowledge Graph'
info: |
  AWRA 2026 Annual Water Resources Conference, Philadelphia, PA (Nov 9-11)
author: Colton Loftus
layout: hero
class: text-left
transition: fade
mdc: true
drawings:
  persist: false
---

# Linking the Fabric
## Persistent Identifiers and the geoconnex Knowledge Graph

<div class="mt-10 text-lg">
Colton Loftus · Geoconnex core developer<br/>
<span class="caption" style="color:#e8f3f7">AWRA Annual Water Resources Conference · Philadelphia · Nov 9-11, 2026</span>
</div>

<div class="absolute left-16 bottom-8 flex items-center gap-5">
  <img src="/cgs/CGS-Logo-Horizontal-White.png" class="h-9" />
  <span style="width:1px;height:30px;background:rgba(255,255,255,.6)"></span>
  <div style="background:#fff;border-radius:10px;padding:5px 12px;display:flex"><img src="/logos/iow.png" style="height:40px" /></div>
</div>

<!--
Open with the one-sentence pitch: geoconnex gives water features a name that every system can agree on.
-->

---
footer: false
---

# Who am I

<div class="grid grid-cols-[230px_1fr] gap-8 mt-6 items-center">
<div>
<img src="/me.webp" style="width:230px;height:230px;object-fit:cover;object-position:50% 20%;border-radius:50%;border:6px solid #46AB9D" />
<div style="width:230px;text-align:center;margin-top:14px;font-family:'District Pro','Trebuchet MS','Segoe UI',sans-serif;font-size:1.5rem;font-weight:700;color:#2C84B9">Colton Loftus</div>
<div style="width:230px;text-align:center;margin-top:2px;font-size:1rem"><a href="mailto:cloftus@lincolninst.edu" style="color:#48535B">cloftus@lincolninst.edu</a></div>
</div>
<div class="space-y-4">
<div style="display:flex;align-items:center;gap:18px"><div style="width:130px;flex:none;display:flex;justify-content:center"><img src="/cgs/CGS-Logo-Horizontal-Color.png" style="width:130px" /></div><div style="flex:1;background:#E4EFF5;border-radius:18px;padding:18px 24px;color:#48535B"><b style="color:#2C84B9">Software engineer, Lincoln Institute of Land Policy's Center for Geospatial Solutions</b><br/>building global water data infrastructure</div></div>
<div style="display:flex;align-items:center;gap:18px"><div style="width:130px;flex:none;display:flex;justify-content:center"><img src="/logos/iow.png" style="width:112px" /></div><div style="flex:1;background:#DDF1EE;border-radius:18px;padding:18px 24px;color:#48535B"><b style="color:#2C84B9">Geoconnex core developer</b>, working alongside Dave Blodgett (USGS) and the <b style="color:#2C84B9">Internet of Water</b> community</div></div>
</div>
</div>

<!--
Frame: what a developer does in this community = keeping identifiers resolving, harvesting data, helping providers publish.
Optional: mention Princeton CS alum, recent talks (FOSS4G 2026, Harvard CGA).
-->

---

# The problem: hydrologic features lack stable representations and links across datasets

<style>
h1 { font-size: 1.85rem !important; line-height: 1.2; }
</style>

<svg viewBox="0 0 900 405" style="width:89%;display:block;margin:0 auto">
  <g stroke="#82848B" stroke-width="2" stroke-dasharray="5 4" fill="none">
    <path d="M90 100 H250"/><path d="M90 250 H250"/><path d="M90 100 V250"/><path d="M250 100 V250"/>
    <path d="M90 100 L250 250"/><path d="M250 100 L90 250"/>
  </g>
  <circle cx="90" cy="100" r="36" fill="#C9DEE8"/><WaterIcon name="gage" :size="44" color="#2C84B9" :x="68" :y="78"/>
  <text x="90" y="28" text-anchor="middle" style="font-size:15px;font-weight:700" fill="#48535B">Gage</text>
  <text x="90" y="45" text-anchor="middle" class="mono" style="font-size:12px" fill="#2C84B9">09361500</text>
  <circle cx="250" cy="100" r="36" fill="#C9DEE8"/><WaterIcon name="river" :size="44" color="#2C84B9" :x="228" :y="78"/>
  <text x="250" y="28" text-anchor="middle" style="font-size:15px;font-weight:700" fill="#48535B">River reach</text>
  <text x="250" y="45" text-anchor="middle" class="mono" style="font-size:12px" fill="#2C84B9">COMID 17624421</text>
  <circle cx="90" cy="250" r="36" fill="#C9DEE8"/><WaterIcon name="dam" :size="44" color="#2C84B9" :x="68" :y="228"/>
  <text x="90" y="308" text-anchor="middle" style="font-size:15px;font-weight:700" fill="#48535B">Dam</text>
  <text x="90" y="325" text-anchor="middle" class="mono" style="font-size:12px" fill="#2C84B9">NID CO01234</text>
  <circle cx="250" cy="250" r="36" fill="#C9DEE8"/><WaterIcon name="aquifer" :size="44" color="#2C84B9" :x="228" :y="228"/>
  <text x="250" y="308" text-anchor="middle" style="font-size:15px;font-weight:700" fill="#48535B">Basin</text>
  <text x="250" y="325" text-anchor="middle" class="mono" style="font-size:12px" fill="#2C84B9">HUC 14080104</text>
  <text x="170" y="374" text-anchor="middle" style="font-size:15px" fill="#82848B">The same river may have different or confusing</text>
  <text x="170" y="394" text-anchor="middle" style="font-size:15px" fill="#82848B">ID relationships across datasets. Hard to query.</text>
  <path d="M340 175 L520 175" stroke="#F9C609" stroke-width="5" marker-end="url(#a)"/>
  <defs><marker id="a" markerWidth="8" markerHeight="8" refX="4" refY="4" orient="auto"><path d="M0 0 L8 4 L0 8z" fill="#F9C609"/></marker></defs>
  <g stroke="#46AB9D" stroke-width="3">
    <path d="M700 175 L610 100"/><path d="M700 175 L810 100"/><path d="M700 175 L610 250"/><path d="M700 175 L810 250"/>
  </g>
  <circle cx="700" cy="175" r="52" fill="#2C84B9"/>
  <text x="700" y="172" text-anchor="middle" fill="#fff" style="font-size:14px;font-weight:700">geoconnex</text><text x="700" y="191" text-anchor="middle" fill="#fff" style="font-size:14px">PID</text>
  <circle cx="610" cy="100" r="36" fill="#86C1E2"/><WaterIcon name="gage" :size="44" color="#fff" :x="588" :y="78"/>
  <text x="610" y="44" text-anchor="middle" style="font-size:15px;font-weight:700" fill="#48535B">Gage</text>
  <circle cx="810" cy="100" r="36" fill="#86C1E2"/><WaterIcon name="dam" :size="44" color="#fff" :x="788" :y="78"/>
  <text x="810" y="44" text-anchor="middle" style="font-size:15px;font-weight:700" fill="#48535B">Dam</text>
  <circle cx="610" cy="250" r="36" fill="#86C1E2"/><WaterIcon name="model" :size="44" color="#fff" :x="588" :y="228"/>
  <text x="610" y="308" text-anchor="middle" style="font-size:15px;font-weight:700" fill="#48535B">Model</text>
  <circle cx="810" cy="250" r="36" fill="#86C1E2"/><WaterIcon name="dataset" :size="44" color="#fff" :x="788" :y="228"/>
  <text x="810" y="308" text-anchor="middle" style="font-size:15px;font-weight:700" fill="#48535B">Dataset</text>
  <text x="710" y="378" text-anchor="middle" style="font-size:16px;font-weight:700" fill="#2C84B9">Common identifier across systems</text>
</svg>

---

# What is Geoconnex?

<svg viewBox="0 0 940 290" class="w-full mt-6">
  <path d="M148 80 H222" stroke="#F9C609" stroke-width="4" marker-end="url(#ar)"/>
  <path d="M338 80 H412" stroke="#F9C609" stroke-width="4" marker-end="url(#ar)"/>
  <path d="M528 80 H602" stroke="#F9C609" stroke-width="4" marker-end="url(#ar)"/>
  <path d="M718 80 H792" stroke="#F9C609" stroke-width="4" marker-end="url(#ar)"/>
  <circle cx="90" cy="80" r="50" fill="#2C84B9"/>
  <WaterIcon name="submit" :size="58" color="#fff" :x="61" :y="51"/>
  <text x="90" y="165" text-anchor="middle" style="font-size:17px;font-weight:700" fill="#48535B">Dataset submission</text>
  <text x="90" y="190" text-anchor="middle" style="font-size:13px" fill="#82848B">provider registers their data</text>
  <text x="90" y="207" text-anchor="middle" style="font-size:13px" fill="#82848B">to the geoconnex registry</text>
  <circle cx="280" cy="80" r="50" fill="#3C97AE"/>
  <WaterIcon name="url" :size="58" color="#fff" :x="251" :y="51"/>
  <text x="280" y="165" text-anchor="middle" style="font-size:17px;font-weight:700" fill="#48535B">Persistent ID</text>
  <text x="280" y="190" text-anchor="middle" style="font-size:13px" fill="#82848B">a stable URL</text>
  <text x="280" y="210" text-anchor="middle" style="font-size:12px" fill="#2C84B9" class="mono">geoconnex.us/ref/…</text>
  <circle cx="470" cy="80" r="50" fill="#46AB9D"/>
  <WaterIcon name="redirect" :size="58" color="#fff" :x="441" :y="51"/>
  <text x="470" y="165" text-anchor="middle" style="font-size:17px;font-weight:700" fill="#48535B">303 Redirect</text>
  <text x="470" y="190" text-anchor="middle" style="font-size:13px" fill="#82848B">sends you to the source</text>
  <circle cx="660" cy="80" r="50" fill="#5BB3B0"/>
  <WaterIcon name="code" :size="58" color="#fff" :x="631" :y="51"/>
  <text x="660" y="165" text-anchor="middle" style="font-size:17px;font-weight:700" fill="#48535B">JSON-LD harvest</text>
  <text x="660" y="190" text-anchor="middle" style="font-size:13px" fill="#82848B">metadata embedded in the page</text>
  <circle cx="850" cy="80" r="50" fill="#86C1E2"/>
  <WaterIcon name="graph" :size="58" color="#48535B" :x="821" :y="51"/>
  <text x="850" y="165" text-anchor="middle" style="font-size:17px;font-weight:700" fill="#48535B">Knowledge graph</text>
  <text x="850" y="190" text-anchor="middle" style="font-size:13px" fill="#82848B">links across organizations</text>
  <text x="850" y="210" text-anchor="middle" style="font-size:12px" fill="#2C84B9" class="mono">graph.geoconnex.us</text>
  <defs><marker id="ar" markerUnits="userSpaceOnUse" markerWidth="12" markerHeight="12" refX="10" refY="6" orient="auto"><path d="M0 0 L12 6 L0 12z" fill="#F9C609"/></marker></defs>
</svg>

<div class="mt-2 text-center text-lg">Providers keep owning their data and can make updates as they see fit. Geoconnex catalogs and links it.</div>

---

# Persistent identifiers

<div class="grid grid-cols-2 gap-8 mt-4">
<div>
<div style="margin-bottom:135px">
<div class="card blue mono" style="font-size:0.9rem;white-space:nowrap;overflow:visible">
<span style="color:#82848B">https://geoconnex.us/</span><span style="position:relative;display:inline-block;color:#46AB9D;font-weight:700">ref<span style="position:absolute;left:50%;top:100%;transform:translateX(-50%);display:flex;flex-direction:column;align-items:center;margin-top:6px">
<svg width="14" height="26" viewBox="0 0 14 26" style="overflow:visible"><path d="M7 26 V3" stroke="#46AB9D" stroke-width="2.5" stroke-linecap=round /><path d="M2 8 L7 2 L12 8" stroke="#46AB9D" stroke-width="2.5" fill="none" stroke-linecap=round stroke-linejoin=round /></svg>
<span style="background:#DDF1EE;color:#46AB9D;border-radius:999px;padding:2px 14px;font-family:Aptos,'Segoe UI',Arial,sans-serif;font-size:.8rem;font-weight:700;white-space:nowrap">namespace</span></span></span><span style="color:#82848B">/</span><span style="position:relative;display:inline-block;color:#2C84B9;font-weight:700">mainstems<span style="position:absolute;left:50%;top:100%;transform:translateX(-50%);display:flex;flex-direction:column;align-items:center;margin-top:6px">
<svg width="14" height="72" viewBox="0 0 14 72" style="overflow:visible"><path d="M7 72 V3" stroke="#2C84B9" stroke-width="2.5" stroke-linecap=round /><path d="M2 8 L7 2 L12 8" stroke="#2C84B9" stroke-width="2.5" fill="none" stroke-linecap=round stroke-linejoin=round /></svg>
<span style="background:#D9E9F3;color:#2C84B9;border-radius:999px;padding:2px 14px;font-family:Aptos,'Segoe UI',Arial,sans-serif;font-size:.8rem;font-weight:700;white-space:nowrap">collection</span></span></span><span style="color:#82848B">/</span><span style="position:relative;display:inline-block;color:#48535B;font-weight:700">35394<span style="position:absolute;left:50%;top:100%;transform:translateX(-50%);display:flex;flex-direction:column;align-items:center;margin-top:6px">
<svg width="14" height="26" viewBox="0 0 14 26" style="overflow:visible"><path d="M7 26 V3" stroke="#48535B" stroke-width="2.5" stroke-linecap=round /><path d="M2 8 L7 2 L12 8" stroke="#48535B" stroke-width="2.5" fill="none" stroke-linecap=round stroke-linejoin=round /></svg>
<span style="background:#E3E8EB;color:#48535B;border-radius:999px;padding:2px 14px;font-family:Aptos,'Segoe UI',Arial,sans-serif;font-size:.8rem;font-weight:700;white-space:nowrap">feature id</span></span></span>
</div>
</div>
<ul class="mt-2">
<li>Stable even when the data moves</li>
<li>Resolvable by any web browser</li>
<li>No prior coordination needed</li>
</ul>
</div>
<svg viewBox="0 0 440 310">
  <circle cx="50" cy="150" r="30" fill="#C9DEE8"/><text x="50" y="155" text-anchor="middle" style="font-size:13px" fill="#48535B">Request</text>
  <rect x="140" y="115" width="110" height="70" rx="14" fill="#2C84B9"/><text x="195" y="145" text-anchor="middle" style="font-size:13px" fill="#fff">geoconnex.us</text><text x="195" y="164" text-anchor="middle" style="font-size:12px" fill="#fff">PID resolver</text>
  <path d="M82 150 H138" stroke="#48535B" stroke-width="3"/>
  <path d="M252 135 Q310 60 353 50" stroke="#F9C609" stroke-width="3" fill="none"/>
  <path d="M252 150 H353" stroke="#F9C609" stroke-width="3" fill="none"/>
  <path d="M252 165 Q310 240 353 250" stroke="#F9C609" stroke-width="3" fill="none"/>
  <g fill="#46AB9D"><circle cx="385" cy="50" r="30"/><circle cx="385" cy="150" r="30"/><circle cx="385" cy="250" r="30"/></g>
  <WaterIcon name="gage" :size="38" color="#fff" :x="366" :y="31"/>
  <WaterIcon name="dam" :size="38" color="#fff" :x="366" :y="131"/>
  <WaterIcon name="reservoir" :size="38" color="#fff" :x="366" :y="231"/>
  <g style="font-size:11px" fill="#48535B" text-anchor="middle"><text x="385" y="95">USGS</text><text x="385" y="195">State</text><text x="385" y="295">Local</text></g>
  <text x="300" y="115" fill="#F9C609" style="font-size:12px;font-weight:700">303</text>
</svg>
</div>

<div class="caption mt-4">The URL never changes; only the redirect target does.</div>

---

# Reference features: the shared backbone

<div class="grid grid-cols-3 gap-4 mt-6">
<div class="card blue flex items-center gap-4"><WaterIcon name="river" :size="46" color="#2C84B9" /><div><b>Mainstems</b><br/><span class="caption">rivers as linear features</span></div></div>
<div class="card  flex items-center gap-4"><WaterIcon name="huc" :size="46" color="#46AB9D" /><div><b>HUCs</b><br/><span class="caption">watershed boundaries</span></div></div>
<div class="card yellow flex items-center gap-4"><WaterIcon name="aquifer" :size="46" color="#2C84B9" /><div><b>Aquifers</b><br/><span class="caption">groundwater units</span></div></div>
<div class="card  flex items-center gap-4"><WaterIcon name="dam" :size="46" color="#46AB9D" /><div><b>Dams</b><br/><span class="caption">infrastructure</span></div></div>
<div class="card blue flex items-center gap-4"><WaterIcon name="gage" :size="46" color="#2C84B9" /><div><b>Gages</b><br/><span class="caption">monitoring locations</span></div></div>
<div class="card yellow flex items-center gap-4"><WaterIcon name="state" :size="46" color="#2C84B9" /><div><b>States &amp; counties</b><br/><span class="caption">administrative geographies</span></div></div>
</div>

<div class="mt-8 text-center">Served via <b>OGC API - Features</b> at <a href="https://reference.geoconnex.us">reference.geoconnex.us</a></div>

<div class="mt-6 text-center" style="padding:8px 28px">
<div style="font-size:1.05rem">Multiple organizations contribute to these <b>common, shared identifiers</b>, which can be reused across</div>
<div class="mt-3 flex justify-center gap-4">
<span style="display:inline-flex;align-items:center;gap:8px;background:#C9DEE8;color:#2C84B9;border-radius:999px;padding:4px 16px 4px 10px;font-weight:700"><WaterIcon name="model" :size="24" color="#2C84B9" />Analytics</span>
<span style="display:inline-flex;align-items:center;gap:8px;background:#C9DEE8;color:#2C84B9;border-radius:999px;padding:4px 16px 4px 10px;font-weight:700"><WaterIcon name="map" :size="24" color="#2C84B9" />Mapping</span>
<span style="display:inline-flex;align-items:center;gap:8px;background:#C9DEE8;color:#2C84B9;border-radius:999px;padding:4px 16px 4px 10px;font-weight:700"><WaterIcon name="graph" :size="24" color="#2C84B9" />Data discovery</span>
</div>
</div>
---

# Controlled vocabularies

<svg viewBox="0 0 900 330" class="w-full mt-2">
  <rect x="20" y="40" width="240" height="64" rx="32" fill="#C9DEE8"/>
  <rect x="28" y="48" width="84" height="48" rx="24" fill="#fff"/>
  <image href="/logos/usgs.svg" x="38.0" y="55.0" width="64" height="34" preserveAspectRatio="xMidYMid meet"/>
  <text x="130" y="78" style="font-size:17px;font-weight:600" fill="#48535B">"Streamflow"</text>
  <rect x="20" y="120" width="240" height="64" rx="32" fill="#C9DEE8"/>
  <rect x="28" y="128" width="84" height="48" rx="24" fill="#fff"/>
  <image href="/logos/usace.svg" x="48.0" y="132.0" width="44" height="40" preserveAspectRatio="xMidYMid meet"/>
  <text x="130" y="158" style="font-size:17px;font-weight:600" fill="#48535B">"Discharge"</text>
  <rect x="20" y="200" width="240" height="64" rx="32" fill="#C9DEE8"/>
  <rect x="28" y="208" width="84" height="48" rx="24" fill="#fff"/>
  <image href="/logos/usbr.jpg" x="54.0" y="212.0" width="32" height="40" preserveAspectRatio="xMidYMid meet"/>
  <text x="130" y="238" style="font-size:17px;font-weight:600" fill="#48535B">"Q (cfs)"</text>
  <text x="140" y="290" text-anchor="middle" style="font-size:14px" fill="#82848B">Each organization's own terms (illustrative)</text>
  <g stroke="#F9C609" stroke-width="3" fill="none"><path d="M262 72 C330 72 330 150 366 150"/><path d="M262 152 H366"/><path d="M262 232 C330 232 330 154 366 154"/></g>
  <circle cx="430" cy="152" r="66" fill="#46AB9D"/>
  <text x="430" y="148" text-anchor="middle" style="font-size:18px;font-weight:700" fill="#fff">SKOS</text>
  <text x="430" y="170" text-anchor="middle" style="font-size:13px" fill="#fff">shared concept</text>
  <path d="M496 140 C540 130 550 70 596 62" stroke="#46AB9D" stroke-width="3" fill="none"/>
  <rect x="598" y="25" width="290" height="70" rx="16" fill="#2C84B9"/>
  <text x="743" y="58" text-anchor="middle" style="font-size:18px;font-weight:700" fill="#fff">Query once, find all</text>
  <text x="743" y="79" text-anchor="middle" style="font-size:13px" fill="#fff">better query performance</text>
  <rect x="598" y="125" width="290" height="80" rx="16" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <circle cx="640" cy="165" r="26" fill="#86C1E2"/><WaterIcon name="person" :size="34" color="#fff" :x="623" :y="148"/>
  <text x="680" y="158" style="font-size:16px;font-weight:700" fill="#48535B">For humans</text>
  <text x="680" y="180" style="font-size:12.5px" fill="#82848B">search by familiar concept,</text>
  <text x="680" y="196" style="font-size:12.5px" fill="#82848B">miss fewer results</text>
  <rect x="598" y="220" width="290" height="80" rx="16" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <circle cx="640" cy="260" r="26" fill="#46AB9D"/><WaterIcon name="ai" :size="34" color="#fff" :x="623" :y="243"/>
  <text x="680" y="253" style="font-size:16px;font-weight:700" fill="#48535B">For AI systems</text>
  <text x="680" y="275" style="font-size:12.5px" fill="#82848B">unambiguous concepts,</text>
  <text x="680" y="291" style="font-size:12.5px" fill="#82848B">more precise queries</text>
</svg>

<div class="text-center mt-2">Organizations <b>keep their own terms</b> and map them to shared concepts.</div>

---

# Linking across federal agencies

<svg viewBox="0 0 900 420" class="w-full">
  <g stroke="#46AB9D" stroke-width="3"><path d="M450 195 L130 70"/><path d="M450 195 L450 40"/><path d="M450 195 L770 70"/><path d="M450 195 L130 300"/><path d="M450 195 L450 350"/><path d="M450 195 L770 300"/></g>
  <circle cx="450" cy="195" r="58" fill="#2C84B9"/>
  <WaterIcon name="river" :size="46" color="#fff" :x="427" :y="160"/>
  <text x="450" y="226" text-anchor="middle" fill="#fff" style="font-size:14px;font-weight:700">Mainstem PID</text>
  <rect x="50" y="34" width="160" height="72" rx="14" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <image href="/logos/usgs.svg" x="65.0" y="40.0" width="130" height="60" preserveAspectRatio="xMidYMid meet"/>
  <text x="130" y="126" text-anchor="middle" style="font-size:14px" fill="#48535B">streamgages</text>
  <rect x="370" y="4" width="160" height="72" rx="14" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <image href="/logos/usace.svg" x="410.0" y="9.0" width="80" height="62" preserveAspectRatio="xMidYMid meet"/>
  <text x="544" y="45" text-anchor="start" style="font-size:14px" fill="#48535B">reservoirs</text>
  <rect x="690" y="34" width="160" height="72" rx="14" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <image href="/logos/nrcs.svg" x="700.0" y="45.0" width="140" height="50" preserveAspectRatio="xMidYMid meet"/>
  <text x="770" y="126" text-anchor="middle" style="font-size:14px" fill="#48535B">snowpack</text>
  <rect x="50" y="264" width="160" height="72" rx="14" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <image href="/logos/noaa.svg" x="98.0" y="268.0" width="64" height="64" preserveAspectRatio="xMidYMid meet"/>
  <text x="130" y="356" text-anchor="middle" style="font-size:14px" fill="#48535B">forecasts</text>
  <rect x="370" y="314" width="160" height="72" rx="14" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <image href="/logos/epa.svg" x="385.0" y="329.0" width="130" height="42" preserveAspectRatio="xMidYMid meet"/>
  <text x="450" y="406" text-anchor="middle" style="font-size:14px" fill="#48535B">water quality</text>
  <rect x="690" y="264" width="160" height="72" rx="14" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <image href="/logos/usbr.jpg" x="745" y="270" width="50" height="60" preserveAspectRatio="xMidYMid meet"/>
  <text x="770" y="356" text-anchor="middle" style="font-size:14px" fill="#48535B">dams</text>
</svg>

<div class="caption text-center">Streamgages, reservoirs, snowpack, forecasts: all pointing at the same river</div>

---
layout: iframe
url: https://internetofwater.github.io/Geoconnex-Feature-UI/
---

<!--
LIVE DEMO. Pick a mainstem, show associated gages, dams, HUCs.
Have a screenshot fallback in case conference wifi fails.
-->

---

# Many ways to access and ingest Geoconnex data

<svg viewBox="0 0 900 330" class="w-full mt-1">
  <rect x="10" y="20" width="280" height="62" rx="16" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <circle cx="46" cy="51" r="21" fill="#2C84B9"/><WaterIcon name="huc" :size="28" color="#fff" :x="32" :y="37"/>
  <text x="78" y="48" style="font-size:15px;font-weight:700" fill="#48535B">Reference features API</text>
  <text x="78" y="66" style="font-size:12px" fill="#82848B">OGC API - Features</text>
  <rect x="10" y="97" width="280" height="62" rx="16" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <circle cx="46" cy="128" r="21" fill="#2C84B9"/><WaterIcon name="gage" :size="28" color="#fff" :x="32" :y="114"/>
  <text x="78" y="125" style="font-size:15px;font-weight:700" fill="#48535B">Feature Search API</text>
  <text x="78" y="143" style="font-size:12px" fill="#82848B">OGC API with free text CQL2 filters</text>
  <rect x="10" y="174" width="280" height="62" rx="16" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <circle cx="46" cy="205" r="21" fill="#2C84B9"/><WaterIcon name="graph" :size="28" color="#fff" :x="32" :y="191"/>
  <text x="78" y="202" style="font-size:15px;font-weight:700" fill="#48535B">Knowledge graph</text>
  <text x="78" y="220" style="font-size:12px" fill="#82848B">SPARQL-based RDF graph endpoint</text>
  <rect x="10" y="251" width="280" height="62" rx="16" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <circle cx="46" cy="282" r="21" fill="#2C84B9"/><WaterIcon name="dataset" :size="28" color="#fff" :x="32" :y="268"/>
  <text x="78" y="279" style="font-size:15px;font-weight:700" fill="#48535B">Data catalog</text>
  <text x="78" y="297" style="font-size:12px" fill="#82848B">STAC · GeoParquet · PMTiles</text>
  <rect x="322" y="20" width="156" height="294" rx="18" fill="#C9DEE8"/>
  <text x="400" y="52" text-anchor="middle" style="font-size:16px;font-weight:700" fill="#2C84B9">Open standards</text>
  <g text-anchor="middle" fill="#48535B">
    <text x="400" y="92" style="font-size:13px;font-weight:700">OGC API - Features</text>
    <text x="400" y="110" style="font-size:11.5px">any compliant tool</text><text x="400" y="125" style="font-size:11.5px">can load features</text>
    <text x="400" y="167" style="font-size:13px;font-weight:700">SPARQL</text>
    <text x="400" y="185" style="font-size:11.5px">one query language</text><text x="400" y="200" style="font-size:11.5px">across the graph</text>
    <text x="400" y="242" style="font-size:13px;font-weight:700">STAC</text>
    <text x="400" y="260" style="font-size:11.5px">standard catalog of</text><text x="400" y="275" style="font-size:11.5px">downloadable data</text>
  </g>
  <g stroke="#F9C609" stroke-width="3.5" fill="none" stroke-linecap="round" stroke-linejoin="round">
    <path d="M294 167 H316 M311 161 L317 167 L311 173"/><path d="M482 167 H504 M499 161 L505 167 L499 173"/>
  </g>
  <rect x="510" y="20" width="180" height="140" rx="16" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <image href="/logos/python.svg" x="574" y="36" width="52" height="52" preserveAspectRatio="xMidYMid meet"/>
  <text x="600" y="118" text-anchor="middle" style="font-size:16px;font-weight:700" fill="#48535B">Python</text>
  <text x="600" y="138" text-anchor="middle" style="font-size:11px" fill="#82848B">API requests, GeoPandas, Agents</text>
  <rect x="705" y="20" width="180" height="140" rx="16" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <image href="/logos/qgis.svg" x="769.0" y="36" width="52" height="52" preserveAspectRatio="xMidYMid meet"/>
  <text x="795" y="118" text-anchor="middle" style="font-size:16px;font-weight:700" fill="#48535B">QGIS</text>
  <text x="795" y="138" text-anchor="middle" style="font-size:11px" fill="#82848B">add as an OGC API layer</text>
  <rect x="510" y="174" width="180" height="140" rx="16" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <image href="/logos/arcgis.svg" x="577.0" y="190" width="46" height="52" preserveAspectRatio="xMidYMid meet"/>
  <text x="600" y="272" text-anchor="middle" style="font-size:16px;font-weight:700" fill="#48535B">ArcGIS</text>
  <text x="600" y="292" text-anchor="middle" style="font-size:11px" fill="#82848B">OGC API feature layers</text>
  <rect x="705" y="174" width="180" height="140" rx="16" fill="#fff" stroke="#C9DEE8" stroke-width="2"/>
  <WaterIcon name="map" :size="52" color="#2C84B9" :x="769" :y="190"/>
  <text x="795" y="272" text-anchor="middle" style="font-size:16px;font-weight:700" fill="#48535B">Web maps</text>
  <text x="795" y="292" text-anchor="middle" style="font-size:11px" fill="#82848B">MapLibre · Leaflet · OpenLayers</text>
</svg>

<div class="text-center mt-1">Geoconnex uses open geospatial standards for wide GIS interoperability</div>

---

# How organizations contribute

<div class="grid grid-cols-2 gap-8 mt-6">
<div class="card blue">
<h3>Bulk integration <span class="pill">recommended</span></h3>
A public container that outputs JSON-LD. No new web infrastructure required.
</div>
<div class="card">
<h3>Crawlable landing pages</h3>
Embed JSON-LD on your own pages and list them in a sitemap.
</div>
</div>

<svg viewBox="0 0 900 110" class="w-full mt-8">
  <g text-anchor="middle" style="font-size:15px;font-weight:700">
    <rect x="10" y="25" width="190" height="60" rx="30" fill="#C9DEE8"/><text x="105" y="61" fill="#48535B">1. Pick PIDs</text>
    <rect x="240" y="25" width="190" height="60" rx="30" fill="#86C1E2"/><text x="335" y="61" fill="#48535B">2. Add metadata</text>
    <rect x="470" y="25" width="190" height="60" rx="30" fill="#46AB9D"/><text x="565" y="61" fill="#fff">3. Open a PR</text>
    <rect x="700" y="25" width="190" height="60" rx="30" fill="#2C84B9"/><text x="795" y="61" fill="#fff">4. Harvested</text>
  </g>
</svg>
<div class="caption text-center">All reviewed via GitHub pull requests at internetofwater/geoconnex.us</div>

---

# Shared benefit for Geoconnex and external agencies: richer data relationships

<style>
h1 { font-size: 1.85rem !important; line-height: 1.2; }
</style>

<div class="mt-3 text-center" style="font-size:1.1rem">Contributing agencies can <b>explore links from their data to other hydrologic datasets</b> and gain insight into <b>other data in the same region</b> with <b>low maintenance burden</b>.</div>

<svg viewBox="0 0 900 330" style="width:86%;display:block;margin:6px auto 0">
  <rect x="225" y="8" width="660" height="316" rx="22" fill="#C9DEE8" fill-opacity=".4" stroke="#86C1E2" stroke-width="2" stroke-dasharray="7 6"/>
  <WaterIcon name="graph" :size="26" color="#2C84B9" :x="243" :y="16"/>
  <text x="276" y="36" style="font-size:15px;font-weight:700" fill="#2C84B9">Existing Geoconnex graph</text>
  <g stroke="#82848B" stroke-width="2.5" fill="none" stroke-linecap="round"><path d="M390 170 L530 75"/><path d="M530 75 L680 60"/><path d="M680 60 L800 135"/><path d="M800 135 L790 255"/><path d="M790 255 L640 270"/><path d="M640 270 L390 170"/><path d="M390 170 L800 135"/></g>
  <path d="M132 170 H342" stroke="#F9C609" stroke-width="5" stroke-linecap="round"/>
  <path d="M328 158 L344 170 L328 182" stroke="#F9C609" stroke-width="5" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
  <text x="236" y="131" text-anchor="middle" style="font-size:13px;font-weight:700" fill="#48535B">links to reference feature</text>
  <text x="236" y="149" text-anchor="middle" style="font-size:12px" fill="#82848B">(Example: Mainstem)</text>
  <circle cx="88" cy="170" r="42" fill="#2C84B9"/><WaterIcon name="gage" :size="52" color="#fff" :x="62" :y="144"/>
  <text x="88" y="238" text-anchor="middle" style="font-size:15px;font-weight:700" fill="#48535B">Your monitoring</text>
  <text x="88" y="256" text-anchor="middle" style="font-size:15px;font-weight:700" fill="#48535B">location</text>
  <circle cx="390" cy="170" r="42" fill="#46AB9D" stroke="#2C84B9" stroke-width="4"/><WaterIcon name="river" :size="46" color="#fff" :x="367" :y="147"/>
  <text x="390" y="236" text-anchor="middle" style="font-size:15px;font-weight:700" fill="#2C84B9">Mainstem</text>
  <circle cx="530" cy="75" r="30" fill="#86C1E2"/><WaterIcon name="gage" :size="36" color="#fff" :x="512" :y="57"/>
  <text x="530" y="125" text-anchor="middle" style="font-size:13px;font-weight:700" fill="#48535B">Upstream gage</text>
  <circle cx="680" cy="60" r="30" fill="#86C1E2"/><WaterIcon name="dam" :size="36" color="#fff" :x="662" :y="42"/>
  <text x="680" y="110" text-anchor="middle" style="font-size:13px;font-weight:700" fill="#48535B">Dam</text>
  <circle cx="800" cy="135" r="30" fill="#86C1E2"/><WaterIcon name="reservoir" :size="36" color="#fff" :x="782" :y="117"/>
  <text x="800" y="185" text-anchor="middle" style="font-size:13px;font-weight:700" fill="#48535B">Reservoir</text>
  <circle cx="790" cy="255" r="30" fill="#86C1E2"/><WaterIcon name="model" :size="36" color="#fff" :x="772" :y="237"/>
  <text x="790" y="305" text-anchor="middle" style="font-size:13px;font-weight:700" fill="#48535B">Model output</text>
  <circle cx="640" cy="270" r="30" fill="#86C1E2"/><WaterIcon name="gage" :size="36" color="#fff" :x="622" :y="252"/>
  <text x="640" y="320" text-anchor="middle" style="font-size:13px;font-weight:700" fill="#48535B">Downstream gage</text>
</svg>

---
layout: hero
---

# Get involved

<div class="grid grid-cols-2 gap-10 mt-6 text-lg">
<div>
<b>Colton Loftus</b><br/>
<a href="mailto:cloftus@lincolninst.edu">cloftus@lincolninst.edu</a>
</div>
<div>
<b>Geoconnex on GitHub</b><br/>
<a href="https://github.com/internetofwater/geoconnex.us">github.com/internetofwater/geoconnex.us</a><br/>
<span class="caption" style="color:#e8f3f7">docs.geoconnex.us</span>
</div>
</div>

<div class="absolute left-16 bottom-8 flex items-center gap-5">
  <img src="/cgs/CGS-Logo-Horizontal-White.png" class="h-9" />
  <span style="width:1px;height:30px;background:rgba(255,255,255,.6)"></span>
  <div style="background:#fff;border-radius:10px;padding:5px 12px;display:flex"><img src="/logos/iow.png" style="height:40px" /></div>
</div>
