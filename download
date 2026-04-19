import { useState, useMemo, useEffect } from "react";

// ── GOOGLE FONTS — matching MGA website ──────────────────────────────────────
const FONT_LINK = "https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;0,700;1,400;1,600&family=Inter:wght@300;400;500;600&family=DM+Mono:wght@400;500&display=swap";

// ── COLOURS — from MGA website ────────────────────────────────────────────────
const C = {
  navy:        "#1C2B3A",              // deep navy — MGA hero background
  gold:        "#B8924A",              // MGA gold — headings and accents
  cream:       "#F8F6F1",              // MGA light section background
  white:       "#FFFFFF",
  muted:       "#6B7C8D",              // subdued text on light
  mutedLight:  "rgba(255,255,255,0.6)",// subdued text on dark
  border:      "rgba(184,146,74,0.18)",// gold-tinted border
  borderLight: "rgba(28,43,58,0.1)",   // subtle border on cream
  green:       "#2A6B4A",
  red:         "#8B2635",
  amber:       "#8B6914",
  light:       "#EDE8DC",              // hover state on cream
  darkAlt:     "#152231",              // darker section variant
};

const ADMIN_PW = "Fajar1982!";

// ── FLAGS ─────────────────────────────────────────────────────────────────────
// Canada: your actual uploaded flag PNG, resized to 40x24px and embedded as base64
// This is the real flag image — no SVG path approximations, no external URLs
const CA_FLAG = "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAYCAMAAAC/Wk/yAAAC7lBMVEXVKx7////65+XmgXnmgXr65eTWMCPWLyL65OLlfHTlfXX54uDWLiLVLSH5393keXHlenL54N743tzkdW3kdm343NrVLSD42tfjcWjjcmn42tjVLB/32NbibmX31dP209DhaWDiamH21NH20M7hZVzhZl31z8z1y8jgYVfgYlj1zcr0ysffX1bfXFL0xsL0xsPfXVPeWlDzwb7zwr/eWE7dVUv//v7yvbnyvrrdU0jcUEb//f3xurbxu7fdUUfcT0TxtrHxt7L//fzcTULbS0D+/Pvwsq3ws67bST7vrqnvr6r++/vbRzzaRTn++vruqqXuq6baRjraRDj++fntpqHup6H++PjaQjfZQDT++Pftopzto53ZQTXZPzP99/bsn5nsn5r99vXZPTHYPDD99PTrmpTrm5X99fTYPDHYOy/98/PqlpDql5H98/LYOS3XNyv88fDqk4zqlI387+7XNyrXNSn87uzpkInpkIr87u3XNinXNCj77ezoi4TojIX76+rXMyfWMib76ejnh4DniIH76unWMiX66Obmg3znhHz65uXWMST65OPmgHj54+H54d/kd2/keHD43dvjdGz429n32dbjcGf319XeVkzqlY/ibGPibWTtpJ7eWk/kd27bSD3xuLT31dL20s/haF7haV/soJr0yMXpjof0ycb88vHgZFvaRjv1zsv1y8fia2LgYFbrmZLrmpPfX1XaQzjzw7/77OvzxMDzxcHfW1HZQTbzwb3eV03dVUrywLzyvLj88O/YOCzrnJbxubXgY1n0x8TcUEXgZFrwtbDojYbcTEHbSj/wsazZPjLdVEnjc2vnhn7qlY7mf3fuqKLuqaP20c7jcmryv7vpj4jxt7PoiYLeWU/mgnvdUkftpJ/tpaDsnpjjb2brmJLpkYvpkovYOi7oi4Pws6/wtLDuqaTnhX3vraj31tTlfnb76efcTkP20M3snZfsoZvvrKfhZ17nhn/vsKvle3P1zMnfXlToioM/tg9UAAAATElEQVR42mNggANGLIABG6ChQhQmFRRi4dBHIQNjDYTNgFchmEIQ+BXiESBdIWERrAacw+drJG4v/uAxRg1VPAFOikIoMRAJd7ApBAA4iANll0NiowAAAABJRU5ErkJggg==";

const Flag = ({ country, h = 22 }) => {
  const w = Math.round(h * 1.5);
  const style = { display:"block", flexShrink:0, borderRadius:2, border:"1px solid rgba(0,0,0,0.12)", width:w, height:h, objectFit:"cover" };
  if (country === "CA") return <img src={CA_FLAG} width={w} height={h} alt="Canada" style={style}/>;
  return (
    <svg width={w} height={h} viewBox="0 0 3 2" style={style}>
      <rect width="3" height="1" fill="#CE1126"/>
      <rect y="1" width="3" height="1" fill="#fff"/>
    </svg>
  );
};



// ── MGA LOGO ──────────────────────────────────────────────────────────────────
const MGALogo = ({ size = 1, light = false }) => {
  const s = size;
  const col = light ? C.white : C.navy;
  const accentCol = C.gold;
  return (
    <div style={{ display:"flex", alignItems:"center", gap:`${12*s}px` }}>
      <div style={{ position:"relative", width:`${38*s}px`, height:`${42*s}px`, flexShrink:0 }}>
        <div style={{ position:"absolute", left:0, top:0, width:`${7*s}px`, height:`${42*s}px`, background:col }}/>
        <div style={{ position:"absolute", right:0, top:0, width:`${7*s}px`, height:`${42*s}px`, background:col }}/>
        <div style={{ position:"absolute", left:0, top:0, width:`${38*s}px`, height:`${7*s}px`, background:col }}/>
        <div style={{ position:"absolute", left:`${9*s}px`, top:`${16*s}px`, width:`${12*s}px`, height:`${12*s}px`, borderRadius:"50%", background:"#3DBDB8" }}/>
      </div>
      <div>
        <div style={{ fontFamily:"'Inter', sans-serif", fontWeight:600, fontSize:`${13*s}px`, letterSpacing:"0.12em", color:col, lineHeight:1.1, textTransform:"uppercase" }}>
          Meridian Gate
        </div>
        <div style={{ fontFamily:"'Inter', sans-serif", fontWeight:300, fontSize:`${9*s}px`, letterSpacing:"0.25em", color: light ? "rgba(255,255,255,0.5)" : C.gold, textTransform:"uppercase", marginTop:`${3*s}px` }}>
          Advisory
        </div>
      </div>
    </div>
  );
};

// ── SMALL UI BITS ─────────────────────────────────────────────────────────────
const SL = ({ t }) => <div style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.54rem", letterSpacing:"0.18em", textTransform:"uppercase", color:C.gold, marginBottom:"0.6rem", opacity:0.8 }}>{t}</div>;
const ConfBadge = ({ c }) => <span style={{ display:"inline-block", padding:"0.1rem 0.42rem", background: c==="V" ? C.green : C.amber, color:"#fff", fontFamily:"'DM Mono',monospace", fontSize:"0.48rem", letterSpacing:"0.08em", textTransform:"uppercase", borderRadius:1 }}>{c==="V" ? "Verified" : "Indicative"}</span>;

const Btn = ({ onClick, children, style={} }) => (
  <button onClick={onClick} style={{ fontFamily:"'DM Sans',sans-serif", cursor:"pointer", border:"none", ...style }}>{children}</button>
);

// ── PRODUCT DATA ──────────────────────────────────────────────────────────────
// ca_* = data when Canada is the IMPORTING country (goods flow ID→CA)
//        = regulatory requirements are CANADIAN import rules; tariffs are what CANADA charges
// id_* = data when Indonesia is the IMPORTING country (goods flow CA→ID)
//        = regulatory requirements are INDONESIAN import rules; tariffs are what INDONESIA charges
//
// CEPA KEY FACTS (verified from official sources, April 2026):
// - Signed September 24, 2025 in Ottawa
// - Target entry into force: 2026 (ratification may extend to early 2027)
// - Canada eliminates 90.5% of tariff lines on Indonesian products
// - Indonesia liberalises 85.8% of its tariff lines on Canadian products
// - Apparel (CH 61/62): phased over 5–15 years from entry into force (NOT immediate)
// - Canola seed/meal: Indonesia eliminates 5% tariff within 10 years
// - Beef (fresh/frozen): Indonesia eliminates 5% within 5 years
// - Potash: Already 0% MFN; CEPA locks in duty-free access
// - Wheat: Already 0% MFN in Indonesia; CEPA secures long-term access

const INITIAL_PRODUCTS = [
  // ── ENERGY ──
  { id:"lng", name:"Liquefied Natural Gas (LNG)", sector:"Energy", hs:"2711.11.00", direction:"BOTH",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA locks in long-term access", ca_conf:"V",
    id_mfn:"0%", id_cepa:"0% (Free)", id_saving:"Already duty-free; CEPA binds access", id_conf:"V",
    ca_reqs:["Canada Energy Regulator (CER) import licence required for large-volume or long-term supply contracts","CBSA standard commercial documentation — invoice, bill of lading, packing list","Environmental assessment required for new import infrastructure (terminals, pipelines)","Transport Canada compliance for marine tanker operations"],
    id_reqs:["BPH Migas (Downstream Oil and Gas Regulatory Authority) approval required for all LNG imports","Pertamina or a licensed gas distributor partnership typically required as the Indonesian buyer","AMDAL (environmental impact assessment) required for new regasification terminal infrastructure","Ministry of Energy and Mineral Resources (ESDM) project clearance"],
    ca_market:"Indonesian LNG from Tangguh and Bontang competes with domestic Canadian supply but can serve niche industrial buyers in Atlantic Canada. Limited opportunity on this direction.",
    id_market:"Indonesia is expanding LNG import capacity for domestic power generation to bridge the gap between declining domestic production and growing demand. Canadian LNG from BC LNG projects (LNG Canada) is well-positioned given CEPA and growing bilateral energy cooperation.",
    ca_score:35, id_score:62 },

  { id:"solar", name:"Solar Panels & Photovoltaic Cells", sector:"Energy", hs:"8541.40.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"5–12%", id_cepa:"0% (Free, phased over 5–10 years under CEPA)", id_saving:"5–12 percentage points as CEPA phases in", id_conf:"I",
    ca_reqs:[], id_reqs:["SNI (Indonesian National Standard) certification required for all electrical equipment sold in Indonesia","BSNI product registration before first importation","API-P (Angka Pengenal Impor Produsen) import licence from Ministry of Trade","TKDN (local content requirement) may apply for government procurement projects — verify current threshold"],
    ca_market:"N/A",
    id_market:"Indonesia's national energy transition targets 23% renewables by 2025 and 31% by 2030, with 4.7 GW of solar planned. Canadian clean-tech exporters (panel manufacturers, inverter producers) are well-positioned. CEPA's clean technology provisions directly support this sector.",
    ca_score:0, id_score:74 },

  { id:"geothermal", name:"Geothermal Equipment & Technology", sector:"Energy", hs:"8412.80.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"5–10%", id_cepa:"0% (Free, phased over 5–10 years under CEPA)", id_saving:"5–10 percentage points as CEPA phases in", id_conf:"I",
    ca_reqs:[], id_reqs:["API-P import licence from Ministry of Trade","SNI certification for electrical and mechanical components","Ministry of Energy (ESDM) project approval at the specific geothermal working area (WKP)","TKDN local content waiver (dispensasi) may be required for imported specialised components"],
    ca_market:"N/A",
    id_market:"Indonesia has 40% of the world's geothermal reserves — the second-largest potential globally. Canadian geothermal technology expertise (from BC and Alberta) is directly applicable. CEPA opens procurement opportunities with PLN and Pertamina Geothermal Energy.",
    ca_score:0, id_score:82 },

  { id:"wind", name:"Wind Turbine Components", sector:"Energy", hs:"8502.31.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–5%", id_cepa:"0% (Free, upon entry into force or phased)", id_saving:"Up to 5 percentage points", id_conf:"I",
    ca_reqs:[], id_reqs:["Ministry of Energy (ESDM) project approval","PLN or independent power producer (IPP) offtake agreement required","API-P import licence","AMDAL (environmental impact assessment) for wind farm site"],
    ca_market:"N/A",
    id_market:"Indonesia's energy transition plan includes expanded wind capacity, particularly in Sulawesi, Nusa Tenggara, and Kalimantan. Canadian clean energy companies are directly targeted in CEPA's clean technology provisions.",
    ca_score:0, id_score:62 },

  // ── FERTILIZERS ──
  { id:"potash", name:"Potash (Potassium Chloride)", sector:"Fertilizers", hs:"3104.20.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0%", id_cepa:"0% (Free)", id_saving:"Already duty-free under MFN; CEPA locks in and binds duty-free access long-term — one of the most significant CEPA wins for Canada", id_conf:"V",
    ca_reqs:[], id_reqs:["Ministry of Agriculture import approval required","PI (registered fertilizer importer) licence required","SNI certification for fertilizer products","Kementan (Ministry of Agriculture) distribution permit","State distributor Pupuk Indonesia coordination for subsidized segment"],
    ca_market:"N/A",
    id_market:"Indonesia imports over 2 million tonnes of potash annually to support its palm oil, rice, and corn sectors. Canada (Saskatchewan) is the world's largest potash producer. CEPA binds duty-free access long-term — a major commercial win for Nutrien and Mosaic.",
    ca_score:0, id_score:92 },

  { id:"phosphate_import", name:"Phosphate Rock & DAP/MAP Fertilizers (Import to Indonesia)", sector:"Fertilizers", hs:"3105.20.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–5%", id_cepa:"0% (Free, phased over 5–15 years under CEPA)", id_saving:"Up to 5 percentage points as CEPA phases in", id_conf:"I",
    ca_reqs:[], id_reqs:["PI fertilizer importer licence","Ministry of Agriculture registration","Kementan distribution permit","Port inspection by BKIPM on arrival"],
    ca_market:"N/A",
    id_market:"Indonesia relies entirely on phosphate rock imports — importing 1.4 million tonnes in 2025 (mostly from Jordan and Algeria). Canadian phosphate producers improve competitiveness under CEPA vs. Moroccan and Chinese suppliers.",
    ca_score:0, id_score:72 },

  { id:"npk_fertilizer", name:"NPK Fertilizers & Processed Phosphate Products (Indonesia Export)", sector:"Fertilizers", hs:"3105.51.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA binds access", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard import documentation","Canada Fertilizers Act registration — fertilizer products must be registered with CFIA before sale","Product label compliance — nutrient content (N-P-K percentages) must be declared on packaging","Transport Canada TDG documentation for bulk shipment"],
    id_reqs:[],
    ca_market:"Indonesia's state-owned fertilizer companies (Pupuk Kaltim, Petrokimia Gresik, Pupuk Indonesia Group) are significant NPK and processed phosphate producers and exporters. While Indonesia imports phosphate rock, it processes and re-exports value-added NPK fertilizer products. Canada's agricultural sector is a potential buyer. This is the relevant entry for Indonesian fertilizer exporters.",
    ca_score:62, id_score:0 },

  { id:"urea", name:"Urea Fertilizer", sector:"Fertilizers", hs:"3102.10.00", direction:"BOTH",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA locks in access", ca_conf:"V",
    id_mfn:"0%", id_cepa:"0% (Free)", id_saving:"Already duty-free; CEPA secures long-term access", id_conf:"V",
    ca_reqs:["CBSA standard import declaration","Transport Canada TDG documentation for bulk urea shipment","Canada Fertilizers Act registration required before sale in Canada","No specific import licence — standard CBSA commercial documentation"],
    id_reqs:["PI fertilizer importer licence","Ministry of Agriculture product registration","Pupuk Indonesia (state distributor) coordination required for subsidized urea segment","Transport documentation for hazardous goods"],
    ca_market:"Indonesia (Pupuk Kaltim, Pupuk Sriwijaya) is a significant urea exporter. Canadian agricultural sector is a potential buyer — Indonesia competes with Middle East and Russian producers.",
    id_market:"Canada is also a urea producer (Nutrien). Two-way trade is possible depending on price arbitrage.",
    ca_score:55, id_score:42 },

  // ── INDONESIA'S TOP EXPORTS TO CANADA (verified from official trade data) ──
  { id:"elec_machinery", name:"Electrical Machinery & Equipment", sector:"Electronics & Machinery", hs:"8537.10.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA binds access", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard import documentation","Industry Canada / ISED electromagnetic compatibility (EMC) certification required for electrical equipment","CSA or ULC safety certification required for most electrical products sold in Canada","Bilingual labelling (EN/FR) required at retail"],
    id_reqs:[],
    ca_market:"Electrical machinery and equipment is Indonesia's #1 export to Canada, worth $675.9M in 2024 — representing 20.5% of all Canadian imports from Indonesia and growing at 22.9% per year over the past decade. This is the single largest Indonesia–Canada trade flow. Includes switchgear, wiring devices, transformers, and industrial control equipment.",
    id_market:"N/A", ca_score:88, id_score:0 },

  { id:"iron_steel", name:"Iron & Steel Products (Hot-Rolled, Rebar, Pipes)", sector:"Minerals & Metals", hs:"7214.20.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA critical minerals provisions apply", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard import documentation","SIMA (Special Import Measures Act) — Canadian steel imports are subject to anti-dumping and countervailing duty investigations; verify current status before contracting","Steel product must meet applicable ASTM or CSA standards for construction use","Country of origin marking required"],
    id_reqs:[],
    ca_market:"Indonesia is the 4th largest steel exporter globally by value (2024), exporting $28B worth of iron and steel worldwide. Indonesia's Krakatau Steel and downstream processors are significant producers. Note: Canadian SIMA trade remedy measures on certain steel products — verify current duty orders before shipping.",
    id_market:"N/A", ca_score:72, id_score:0 },

  { id:"vehicles_parts", name:"Vehicles & Automotive Components (Indonesian-made)", sector:"Automotive", hs:"8703.22.00", direction:"ID→CA",
    ca_mfn:"6.1%", ca_cepa:"0% (Free, phased over 5–15 years)", ca_saving:"6.1 percentage points phased over 5–15 years", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["Transport Canada Motor Vehicle Safety Act (MVSA) — all vehicles must meet Canadian Motor Vehicle Safety Standards (CMVSS)","CBSA standard import documentation","RIV (Registrar of Imported Vehicles) process for vehicles not originally sold in Canada","Recall compliance verification required","Rules of origin: substantial manufacturing must occur in Indonesia for CEPA rates to apply"],
    id_reqs:[],
    ca_market:"Indonesia assembles vehicles for Toyota, Honda, Mitsubishi, Daihatsu, Suzuki. Indonesian-made vehicles and components represent a growing potential export. CEPA tariff elimination (phased over 5–15 years) progressively opens the Canadian market.",
    id_market:"N/A", ca_score:65, id_score:0 },

  { id:"coal", name:"Thermal Coal", sector:"Energy", hs:"2701.12.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard import declaration","Provincial environmental permits may apply depending on end use","Declining market — Canada's coal-fired power is being phased out by 2030 under federal policy","Marine transport compliance required"],
    id_reqs:[],
    ca_market:"Indonesia is the world's largest thermal coal exporter ($31B in 2024). However, Canada's coal-fired power phase-out by 2030 means the Canadian market is structurally declining. Metallurgical coal is a different market — Indonesia primarily exports thermal. Limited opportunity but possible for industrial buyers.",
    id_market:"N/A", ca_score:22, id_score:0 },

  { id:"rubber_products", name:"Rubber Products & Manufactured Rubber Goods", sector:"Rubber & Plastics", hs:"4016.99.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA binds access", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard import documentation","Consumer Product Safety Act compliance for consumer rubber goods","REACH-equivalent chemical compliance documentation required by industrial buyers","No specific import licence required"],
    id_reqs:[],
    ca_market:"Rubber is Canada's 2nd largest import from Indonesia ($265.2M in 2024). Indonesia is the world's 2nd largest natural rubber producer. Products include natural rubber sheets, manufactured rubber parts, hoses, seals, and technical rubber goods serving automotive, construction, and industrial sectors.",
    id_market:"N/A", ca_score:82, id_score:0 },

  { id:"precious_metals_gems", name:"Precious Metals, Gems & Jewellery", sector:"Minerals & Metals", hs:"7113.19.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard commercial documentation — invoice must state metal purity, gemstone type, country of origin","FINTRAC registration required for dealers in precious metals — transactions over CAD $10,000 must be reported","Kimberley Process Certification Scheme (KPCS) for diamonds","AML due diligence required"],
    id_reqs:[],
    ca_market:"Precious stones, metals and jewellery is one of Canada's top 5 imports from Indonesia. Indonesia produces gold (Grasberg mine), silver, and is a significant jewellery manufacturer. Bali filigree gold and silver work are internationally recognized.",
    id_market:"N/A", ca_score:72, id_score:0 },

  { id:"palm_derivatives", name:"Processed Palm Derivatives (Olein, Stearin, PKO)", sector:"Vegetable Oils", hs:"1511.90.10", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA locks in access", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA import licence for refined edible oils","Health Canada food standards compliance","RSPO (Roundtable on Sustainable Palm Oil) supply chain certification required by major Canadian food manufacturers","Phytosanitary certificate from BARANTAN"],
    id_reqs:[],
    ca_market:"Processed palm derivatives (refined olein, stearin, palm kernel oil) are used extensively in Canadian food manufacturing, margarine, confectionery, and personal care products. Indonesia is the world's largest exporter. CEPA eliminates tariffs on palm derivatives — a major CEPA benefit for Indonesia.",
    id_market:"N/A", ca_score:68, id_score:0 },

  // ── SEAFOOD ──
  { id:"shrimp_frozen", name:"Frozen Shrimp (Vannamei & Tiger)", sector:"Seafood", hs:"0306.17.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free under MFN; CEPA binds and locks in preferential access long-term", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA (Canadian Food Inspection Agency) import licence — mandatory for all commercial seafood imports","Health Canada maximum residue limits for veterinary drugs — chloramphenicol and nitrofurans are CFIA priority tests; positive results result in shipment rejection","Cold chain documentation required — temperature log from processing to Canadian border (must remain at -18°C or below)","HACCP certification of Indonesian processing facility must be recognised by CFIA — facility must appear on the approved establishment list","Bilingual labelling (EN/FR) — species common name, country of origin, net weight, best-before date required at retail"],
    id_reqs:[],
    ca_market:"Canada imports over CAD $400M in shrimp annually. Indonesia is already among the top suppliers. Vannamei shrimp from Sumatra and Java is highly competitive on price. Antibiotic-free certification and CFIA-approved facility status are the two practical market access requirements.",
    id_market:"N/A", ca_score:85, id_score:0 },

  { id:"tuna_canned", name:"Canned Tuna", sector:"Seafood", hs:"1604.14.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA binds preferential access", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA Fish Inspection Regulations compliance — Indonesian processing facility must be on the CFIA approved establishment list","Health Canada food additive and preservative standards — all additives must comply with the Food and Drug Regulations","Bilingual label (EN/FR) — common name (e.g. 'skipjack tuna'), ingredients, net weight, best-before, country of origin all required","MSC (Marine Stewardship Council) certification is now required by Loblaw, Sobeys, Metro, and Costco — effectively a commercial market access requirement"],
    id_reqs:[],
    ca_market:"Indonesia is the world's second-largest tuna producer. Bitung (North Sulawesi) and Ambon are the major processing hubs. MSC certification from these facilities significantly opens Canadian retail buyer access. Strong demand in both retail and foodservice channels.",
    id_market:"N/A", ca_score:80, id_score:0 },

  { id:"tuna_fresh", name:"Fresh & Chilled Tuna Loins", sector:"Seafood", hs:"0302.39.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA import licence — seafood for human consumption","Cold chain integrity — product must be maintained at 0–4°C throughout the entire supply chain from processing to delivery","HACCP certification of processing facility recognised by CFIA","Certificate of origin from BKIPM (Indonesian Quarantine Agency) required","Air freight only — sea transit time incompatible with fresh tuna shelf life; target 2–3 day total transit"],
    id_reqs:[],
    ca_market:"Canadian sushi and sashimi market is growing rapidly driven by Japanese restaurant proliferation and mainstream adoption. Indonesian yellowfin and bigeye tuna from Sulawesi and Maluku command premium pricing. Supply chain speed is the primary operational challenge.",
    id_market:"N/A", ca_score:72, id_score:0 },

  { id:"crab", name:"Mud Crab (Frozen & Live)", sector:"Seafood", hs:"0306.24.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; note: crab is one of the products Indonesia carved out from its own CEPA tariff concessions but Canadian import tariffs remain 0%", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA import licence and processing facility approval — facility must be on approved list","Cold chain documentation throughout transit","HACCP certification of Indonesian processing facility","Species identification required — Scylla serrata (mud crab/kepiting) is the most common Indonesian export species","Live crab: DFO (Fisheries and Oceans Canada) aquatic animal health certificate required; inspection at first port of entry"],
    id_reqs:[],
    ca_market:"Indonesian mud crab (kepiting) is well-regarded in the Canadian Asian market. Vancouver and Toronto's Chinese and Southeast Asian restaurant sectors are the primary buyers. Strong demand and limited domestic competition.",
    id_market:"N/A", ca_score:70, id_score:0 },

  { id:"seaweed", name:"Dried Seaweed & Carrageenan", sector:"Seafood", hs:"1212.21.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements — must be free from adulteration, prohibited substances, and pest infestation","Contaminant testing required — heavy metals (arsenic, cadmium, lead) and iodine levels must meet Canadian standards","Phytosanitary certificate from BARANTAN (Indonesian Agricultural Quarantine Agency)","Bilingual labelling (EN/FR) at retail — species name, net weight, origin required"],
    id_reqs:[],
    ca_market:"Indonesia is the world's largest seaweed producer. Canadian food manufacturers use carrageenan (extracted from seaweed) extensively as a food additive. Growing consumer demand for dried seaweed snacks in the health food retail channel.",
    id_market:"N/A", ca_score:68, id_score:0 },

  { id:"salmon", name:"Atlantic Salmon (Fresh & Frozen)", sector:"Seafood", hs:"0302.12.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"5%", id_cepa:"0% (Free, upon CEPA entry into force)", id_saving:"5 percentage points immediately upon entry into force", id_conf:"I",
    ca_reqs:[], id_reqs:["BKIPM (Indonesian Quarantine Agency for Fisheries) import permit required","Health and sanitation certificate from CFIA required — recognised by BKIPM","Halal certification required for all food products sold through Indonesian retail and food service channels — no exceptions","Cold chain documentation — frozen at -18°C, fresh at 0–4°C throughout transit and at border"],
    ca_market:"N/A",
    id_market:"Indonesia's growing middle class and rapidly expanding hotel, restaurant, and catering sector creates strong demand for premium imported salmon. Canadian Maritime salmon from New Brunswick and Nova Scotia, and BC salmon from Pacific operations, are both relevant. Halal certification is the primary market access requirement and must be obtained before shipment.",
    ca_score:0, id_score:72 },

  { id:"lobster", name:"Live & Frozen Lobster", sector:"Seafood", hs:"0306.11.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"5%", id_cepa:"0% (Free, upon CEPA entry into force)", id_saving:"5 percentage points upon entry into force", id_conf:"I",
    ca_reqs:[], id_reqs:["BKIPM import permit","Health certificate from CFIA recognised by BKIPM","Halal certification required for foodservice channel","Specialised cold-chain logistics for live lobster — tank systems and oxygen required","Air freight only for live product — target 24–36 hour transit"],
    ca_market:"N/A",
    id_market:"Canadian Maritime lobster (Homarus americanus) is a premium product in Indonesian five-star hotels and fine dining. CEPA tariff elimination improves price competitiveness vs. Australian and US lobster. Vancouver and Halifax are the main export points.",
    ca_score:0, id_score:65 },

  // ── VEGETABLE OILS ──
  { id:"palm_oil", name:"Crude Palm Oil (CPO)", sector:"Vegetable Oils", hs:"1511.10.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA locks in preferential access", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA licence required for edible oils destined for human consumption","Health Canada compositional standards for food-grade palm oil must be met","RSPO (Roundtable on Sustainable Palm Oil) certification now effectively required by major Canadian food manufacturers and retailers — commercial rather than regulatory requirement","Phytosanitary certificate from BARANTAN required"],
    id_reqs:[],
    ca_market:"Canada's food manufacturing and personal care sectors are steady consumers of palm oil. RSPO sustainability certification is the primary commercial differentiator — without it, major Canadian buyers (Unilever, Nestlé, Loblaw) will not source.",
    id_market:"N/A", ca_score:62, id_score:0 },

  { id:"coconut_oil", name:"Coconut Oil (Virgin & RBD)", sector:"Vegetable Oils", hs:"1513.11.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements — must meet Health Canada compositional standards for coconut oil","Organic certification under Canada Organic Regime (COR) if marketed as organic — significant price premium","Country of origin and bilingual product labelling (EN/FR) required at retail","Phytosanitary certificate for virgin/minimally processed coconut oil"],
    id_reqs:[],
    ca_market:"Canadian demand for virgin coconut oil in health food, natural cosmetics, and cooking is strong and growing. Indonesian VCO from Sulawesi and North Maluku competes well with Philippine product. Organic certification commands a 30–50% price premium.",
    id_market:"N/A", ca_score:74, id_score:0 },

  { id:"canola_oil", name:"Canola Oil (Refined)", sector:"Vegetable Oils", hs:"1514.11.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"5%", id_cepa:"0% (Free, upon entry into force under CEPA — confirmed)", id_saving:"5 percentage points immediately upon CEPA entry into force", id_conf:"V",
    ca_reqs:[], id_reqs:["BPOM food import registration (ML number) required before first shipment","PI import licence from Ministry of Trade","Halal certification (MUI) required for all food products sold in Indonesia","Indonesian language labelling required on all retail packaging","RSPO or equivalent sustainability certification preferred by large Indonesian food manufacturers"],
    ca_market:"N/A",
    id_market:"Indonesia's vast cooking oil market is dominated by palm oil but has a growing premium segment for healthier alternatives. Canadian canola oil serves health-conscious consumers and food manufacturers. CEPA's immediate 5% tariff elimination upon entry into force improves competitiveness.",
    ca_score:0, id_score:62 },

  // ── GRAINS & AGRICULTURE ──
  { id:"wheat", name:"Wheat & Wheat Flour", sector:"Grains & Agriculture", hs:"1001.99.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0%", id_cepa:"0% (Free)", id_saving:"Already duty-free under MFN; CEPA provides binding long-term access — locks in duty-free status", id_conf:"V",
    ca_reqs:[], id_reqs:["BPOM (National Agency of Drug and Food Control) import approval required before shipment of processed wheat products","PI (importir) licence from Ministry of Trade required","Phytosanitary certificate from CFIA required for all grain and flour shipments to Indonesia","Halal certification required for wheat flour destined for food use in Indonesia"],
    ca_market:"N/A",
    id_market:"Indonesia is the world's second-largest wheat importer, consuming over 10 million tonnes annually for its noodle, bread, and biscuit industries. Canadian hard red spring wheat from the Prairies is highly regarded for its protein content. CEPA locks in duty-free access that was already the status quo, providing long-term commercial predictability.",
    ca_score:0, id_score:94 },

  { id:"soybeans", name:"Soybeans & Soy Products", sector:"Grains & Agriculture", hs:"1201.90.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0%", id_cepa:"0% (Free)", id_saving:"Already duty-free; CEPA locks in long-term preferential access", id_conf:"V",
    ca_reqs:[], id_reqs:["BPOM import approval for food-use soybeans and soy-derived products","PI import licence from Ministry of Trade","Phytosanitary certificate from CFIA required for all soybean shipments","GMO labelling compliance required under Indonesian food law — GMO status must be declared on import documentation"],
    ca_market:"N/A",
    id_market:"Indonesia is a major soybean importer for its tofu, tempeh, and soy sauce industries. Canada is a significant soybean producer. Non-GMO premium commands higher prices in Indonesian market, particularly for the traditional tofu and tempeh sector.",
    ca_score:0, id_score:82 },

  { id:"canola_seeds", name:"Canola Seeds & Canola Meal", sector:"Grains & Agriculture", hs:"1205.10.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"5%", id_cepa:"0% (Free, phased over 10 years — confirmed under CEPA)", id_saving:"5 percentage points phased over 10 years from CEPA entry into force", id_conf:"V",
    ca_reqs:[], id_reqs:["Phytosanitary certificate from CFIA required for all seed and meal shipments","Ministry of Agriculture import approval","GMO status declaration required on import documentation","PI import licence from Ministry of Trade"],
    ca_market:"N/A",
    id_market:"Indonesia's oilseed crushing industry can process Canadian canola seed, and the aquaculture and poultry sectors use canola meal as animal feed. Canada is the world's largest canola exporter. Note: CEPA phases out the 5% tariff over 10 years rather than immediately.",
    ca_score:0, id_score:60 },

  { id:"beef", name:"Beef & Beef Products", sector:"Meat & Protein", hs:"0202.30.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"5%", id_cepa:"0% (Free, phased over 5 years — confirmed under CEPA)", id_saving:"5 percentage points eliminated within 5 years of CEPA entry into force", id_conf:"V",
    ca_reqs:[], id_reqs:["Halal certification (MUI — Majelis Ulama Indonesia) is absolutely mandatory — no exceptions for any beef product sold in Indonesia","BKIPM import permit from Ministry of Marine Affairs and Fisheries required","Veterinary health certificate from CFIA required and must be recognised by Indonesia's Ministry of Agriculture","Cold chain documentation required throughout transit — temperature logs mandatory","Indonesia's beef import quota system: quotas are allocated to registered importers — verify current quota availability before signing contracts, as the system changes frequently"],
    ca_market:"N/A",
    id_market:"Indonesia's growing middle class consumes more beef. The CEPA specifically includes an SPS MOU addressing beef market access, making this a priority product for bilateral trade. CEPA eliminates the 5% tariff within 5 years of entry into force. Halal certification is non-negotiable.",
    ca_score:0, id_score:65 },

  { id:"dairy", name:"Dairy Products (Cheese, Butter, Milk Powder)", sector:"Meat & Protein", hs:"0402.21.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–5%", id_cepa:"0% (Free, phased over 5–10 years under CEPA)", id_saving:"Up to 5 percentage points as CEPA phases in", id_conf:"I",
    ca_reqs:[], id_reqs:["BKIPM import permit required for all animal-derived products including dairy","BPOM food registration (ML number) required for processed dairy products","Halal certification (MUI) required — dairy must be produced in halal-certified facilities","Veterinary health certificate from CFIA required","Cold chain documentation throughout transit"],
    ca_market:"N/A",
    id_market:"Indonesia imports significant volumes of dairy for its food manufacturing sector. Canadian dairy faces supply management constraints domestically, but processors can export surplus. Halal and BPOM registration are the two primary entry requirements.",
    ca_score:0, id_score:60 },

  // ── COFFEE & BEVERAGES ──
  { id:"coffee_arabica", name:"Arabica Coffee Beans (Green)", sector:"Coffee & Beverages", hs:"0901.11.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA locks in preferential access", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food safety requirements — product must be free of adulteration and contamination","Phytosanitary certificate from BBKP (Indonesian plant quarantine authority) required","Specialty certification (Fair Trade, Rainforest Alliance, Organic) adds significant commercial value and commands price premiums in Canadian market","Cupping score documentation required by Canadian specialty roasters — Q Grader assessment preferred","Traceability to cooperative or farm level expected by third-wave roasters"],
    id_reqs:[],
    ca_market:"Gayo (Aceh) and Flores Arabica are among the most well-regarded Indonesian origins in the Canadian specialty segment. Third-wave roasters in Vancouver, Toronto, Calgary, and Montreal are active buyers. Canada is among the fastest-growing specialty coffee markets globally.",
    id_market:"N/A", ca_score:78, id_score:0 },

  { id:"coffee_robusta", name:"Robusta Coffee Beans (Green)", sector:"Coffee & Beverages", hs:"0901.11.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food safety requirements","Phytosanitary certificate from Indonesian plant quarantine authority required","Commercial invoice must state species (Coffea canephora), origin region, processing method, and weight","Specialty buyers require full traceability to cooperative or farm level and pre-shipment sample approval"],
    id_reqs:[],
    ca_market:"Indonesian Robusta from Sumatra (Lampung) and Sulawesi is well-regarded for espresso and instant coffee blends. Canada's large Italian-Canadian and Portuguese-Canadian communities are strong Robusta consumers. Growing demand from commercial roasters.",
    id_market:"N/A", ca_score:71, id_score:0 },

  { id:"cocoa_beans", name:"Cocoa Beans (Raw)", sector:"Coffee & Beverages", hs:"1801.00.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements — free from adulteration and contamination","Phytosanitary certificate from BARANTAN required","Moisture content (max 7.5%) and quality grading documentation required by buyers","Ochratoxin A (OTA) mycotoxin testing required — Canadian importers increasingly require OTA test results with each shipment"],
    id_reqs:[],
    ca_market:"Canada's craft chocolate (bean-to-bar) sector is a growing buyer for single-origin Indonesian cocoa. Sulawesi (Palu, Luwu Utara) and Flores origins command premiums. Vancouver and Toronto have active craft chocolate communities.",
    id_market:"N/A", ca_score:70, id_score:0 },

  { id:"cocoa_butter", name:"Cocoa Butter", sector:"Coffee & Beverages", hs:"1804.00.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food standards compliance — must meet CODEX Stan 86 compositional requirements for cocoa butter","Certificate of analysis from accredited laboratory required — fat content, free fatty acid content, moisture all specified","BPOM food-grade export certificate recommended","Cold storage during transport — cocoa butter oxidises rapidly if not stored correctly"],
    id_reqs:[],
    ca_market:"Canada's chocolate manufacturing and cosmetics sectors are steady importers. Indonesian cocoa butter from Sulawesi is well-regarded in the craft chocolate segment for its distinctive flavour profile.",
    id_market:"N/A", ca_score:69, id_score:0 },

  { id:"tea", name:"Black & Green Tea (Loose Leaf)", sector:"Coffee & Beverages", hs:"0902.30.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements — free from adulteration","Pesticide residue testing against Canadian MRL (Maximum Residue Limits) — CFIA may test at border","Phytosanitary certificate from BBKP required","Canada Organic Regime (COR) certification for premium organic segment"],
    id_reqs:[],
    ca_market:"Indonesian tea from West Java (Ciwidey, Pangalengan) and Sumatra competes with Sri Lankan and Indian teas. Specialty and organic segments offer the best growth pathway in the Canadian market.",
    id_market:"N/A", ca_score:56, id_score:0 },

  // ── FOOD PROCESSING ──
  { id:"spices", name:"Spices (Pepper, Cloves, Nutmeg, Mace)", sector:"Food & Spices", hs:"0904.11.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements — free from adulteration, filth, and prohibited substances","Phytosanitary certificate from BARANTAN required for all spice shipments","Pesticide residue testing against Canadian MRL — CFIA actively monitors spice imports","Aflatoxin testing required for nutmeg, mace, and pepper — Canadian limits are strict (B1+B2+G1+G2 ≤ 20 ppb)","Bilingual labelling (EN/FR) at retail — common name, net weight, origin, best-before date required"],
    id_reqs:[],
    ca_market:"Indonesia is the world's largest producer of cloves and nutmeg, and a major pepper producer. Canadian food manufacturing and ethnic retail are strong buyers. Quality consistency and food safety certification (especially aflatoxin) are the key commercial requirements.",
    id_market:"N/A", ca_score:72, id_score:0 },

  { id:"noodles", name:"Instant Noodles & Pasta Products", sector:"Food Processing", hs:"1902.30.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements — must comply with Food and Drug Regulations","Bilingual labelling (EN/FR) mandatory — full ingredient list, allergen declarations, net weight, best-before, country of origin","Nutrition Facts table in Canadian prescribed format required","All food additives including flavour enhancers and preservatives must be within Canadian approved limits","Allergen declaration: wheat, soy, shellfish flavouring must be clearly labelled"],
    id_reqs:[],
    ca_market:"Indomie is already one of the top-selling instant noodle brands in Canadian ethnic grocery. Strong growth potential in mainstream supermarket channels. Labelling compliance is the primary market access requirement for smaller Indonesian brands.",
    id_market:"N/A", ca_score:82, id_score:0 },

  { id:"sauces", name:"Sauces, Condiments & Sambal", sector:"Food Processing", hs:"2103.90.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements — must comply with Food and Drug Regulations","Bilingual labelling (EN/FR) mandatory — all ingredients declared in both languages","Nutrition Facts table in Canadian prescribed format required","Food additive compliance — preservatives (benzoates, sorbates) must be within Canadian approved limits","Allergen declaration mandatory — shellfish, soy, wheat (soy sauce) all common allergens in Indonesian condiments"],
    id_reqs:[],
    ca_market:"Growing Canadian demand for Asian condiments driven by multicultural demographics. Indonesian sambal, kecap manis, and chilli sauces have strong market positioning. Major grocery chains (Loblaws, Sobeys, T&T) are expanding ethnic sauce ranges. Bilingual labelling is the most common compliance failure for new entrants.",
    id_market:"N/A", ca_score:75, id_score:0 },

  { id:"bird_nest", name:"Edible Bird's Nests", sector:"Food & Specialty", hs:"0410.10.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"CEPA SPS MOU specifically creates a bilateral dialogue mechanism for this product — directly referenced in the Canada-Indonesia CEPA text", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA import permit specifically for edible bird's nests — this is not covered by standard food import licence","CEPA SPS MOU creates a specific bilateral dialogue channel for this product — Canadian and Indonesian authorities committed to facilitating trade","H5N1 avian influenza testing required — product must test negative before shipment","Product must be registered and inspected at origin by BKIPM before export","Processing facility must meet CFIA requirements for avian products"],
    id_reqs:[],
    ca_market:"Edible bird's nests are specifically mentioned in the CEPA SPS MOU as a priority product for Canada-Indonesia bilateral facilitation. Canadian Chinese and Southeast Asian communities are established buyers. Vancouver and Toronto have active wholesale and retail markets.",
    id_market:"N/A", ca_score:70, id_score:0 },

  { id:"honey", name:"Natural Honey", sector:"Food & Specialty", hs:"0409.00.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA honey import requirements — must meet compositional standards: max 20% water content, max 40 mg/kg HMF","Antibiotic residue testing mandatory — chloramphenicol and streptomycin are the two CFIA priority tests; positive results result in rejection","Country of origin declaration required at border","Bilingual labelling (EN/FR) at retail — net weight, best-before date, country of origin"],
    id_reqs:[],
    ca_market:"Indonesian forest honey (multiflora, tualang) and stingless bee honey (kelulut) are premium specialty products in Canada's natural health retail sector. Antibiotic-free certification is the critical commercial requirement for Canadian buyers.",
    id_market:"N/A", ca_score:62, id_score:0 },

  { id:"snack_foods", name:"Snack Foods (Kerupuk, Rice Crackers, Tempeh Chips)", sector:"Food Processing", hs:"1905.90.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements","Bilingual labelling (EN/FR) mandatory — all ingredients including flavourings and additives declared","Allergen declaration required — shrimp crackers (kerupuk udang) contain shellfish which must be declared prominently","Nutrition Facts table in Canadian prescribed format required","Palm oil used in frying must comply with Canadian edible oil standards"],
    id_reqs:[],
    ca_market:"Indonesian snack foods (kerupuk udang, tempeh chips, rice crackers) have growing presence in Canadian ethnic and health food retail. T&T Supermarket, Nations Fresh Foods, and specialty importers are key distribution channels. Allergen labelling for shellfish-containing kerupuk is the most common compliance issue.",
    id_market:"N/A", ca_score:68, id_score:0 },

  { id:"tofu_tempeh", name:"Tofu & Tempeh Products", sector:"Food Processing", hs:"2106.10.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements — must comply with Food and Drug Regulations","Refrigerated cold chain for fresh products — maintained at 0–4°C throughout transit","Use-by date compliance — fresh tofu/tempeh has short shelf life; air freight typically required","Bilingual labelling (EN/FR) — ingredients, best-before date, storage instructions"],
    id_reqs:[],
    ca_market:"Canada's plant-based protein market is one of the fastest growing globally. Indonesian-style tempeh (with its distinct fermentation profile) is gaining traction in Canadian health food retail. Growing mainstream retail presence alongside existing ethnic grocery distribution.",
    id_market:"N/A", ca_score:70, id_score:0 },

  { id:"packaged_food", name:"Packaged & Processed Foods (Canadian exports)", sector:"Food Processing", hs:"2106.90.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"5–15%", id_cepa:"0% (Free, phased over 5–10 years under CEPA)", id_saving:"5–15 percentage points as CEPA phases in", id_conf:"I",
    ca_reqs:[], id_reqs:["BPOM food registration mandatory — ML (imported product) number must be obtained before first shipment; registration takes 3–9 months","Halal certification (MUI) mandatory for the vast majority of food products sold in Indonesia — no exceptions for Muslim consumer products","Indonesian language labelling required on all retail packaging — all ingredients and instructions in Bahasa Indonesia","Minimum remaining shelf life of 2/3 of total shelf life upon arrival at Indonesian port","No prohibited ingredients under Indonesian food law — pork-derived ingredients require special halal certification"],
    ca_market:"N/A",
    id_market:"Indonesia's modern retail sector (Alfamart, Indomaret, Hypermart, premium supermarkets) provides distribution access for Canadian packaged food brands. Halal certification and BPOM registration are the two non-negotiable market entry requirements.",
    ca_score:0, id_score:62 },

  // ── TEXTILES & APPAREL ──
  { id:"batik", name:"Batik Fabric (Cotton)", sector:"Textiles & Apparel", hs:"5208.31.00", direction:"ID→CA",
    ca_mfn:"18%", ca_cepa:"0% (Free, phased over 5–15 years — NOT immediate)", ca_saving:"18 percentage points phased over 5–15 years from CEPA entry into force", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["Canada's Textile Labelling Act — fibre content (e.g. '100% Cotton') must appear in both English and French on all items","Care instructions label required in both English and French — Canadian law requires specific care symbols","Country of origin label required — 'Made in Indonesia' or 'Produit d'Indonésie'","Rules of origin under CEPA: substantial transformation (cut-and-sew rule) must occur in Indonesia for CEPA rates to apply","No import licence required — standard CBSA commercial invoice and packing list sufficient","Note: CEPA tariff elimination is phased over 5–15 years, not immediate — MFN rate of 18% applies until phase-out occurs"],
    id_reqs:[],
    ca_market:"Canada's multicultural consumer base and sustainable/artisan fashion movement create genuine demand. UNESCO recognition of batik provides strong brand differentiation. Direct-to-retail and e-commerce channels are both viable. Note: the 18% tariff phasing out over time (not immediately) affects the short-term pricing equation.",
    id_market:"N/A", ca_score:65, id_score:0 },

  { id:"garments_cotton", name:"Cotton Garments & Apparel", sector:"Textiles & Apparel", hs:"6109.10.00", direction:"ID→CA",
    ca_mfn:"18%", ca_cepa:"0% (Free, phased over 5–15 years — NOT immediate under CEPA)", ca_saving:"18 percentage points phased over 5–15 years from CEPA entry into force — one of the largest eventual savings", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["Textile Labelling Act compliance — fibre content label in English and French on all garments","Rules of origin under CEPA: cut-and-sew rule must be satisfied — garment must be cut and sewn in Indonesia from any fabric origin","Care label in both English and French required (specific washing, drying, ironing symbols)","No import licence — standard CBSA commercial invoice, packing list, certificate of origin required","Important: CEPA tariff phase-out on apparel is 5–15 years, not immediate — the current 18% MFN rate continues to apply until each specific product's phase-out schedule kicks in"],
    id_reqs:[],
    ca_market:"Indonesia is a major global garment exporter serving brands like H&M, Zara, Gap. The eventual 18% → 0% tariff reduction is commercially significant but phased over time. Canadian fashion retail and e-commerce channels are accessible entry points for Indonesian manufacturers.",
    id_market:"N/A", ca_score:72, id_score:0 },

  { id:"footwear", name:"Leather & Synthetic Footwear", sector:"Textiles & Apparel", hs:"6403.99.00", direction:"ID→CA",
    ca_mfn:"18–20%", ca_cepa:"0% (Free, phased over 5–15 years — NOT immediate)", ca_saving:"18–20 percentage points phased over 5–15 years — one of the largest eventual tariff savings under CEPA", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["Consumer Product Safety Act (CCPSA) compliance — no hazardous materials in materials or coatings","Rules of origin under CEPA: footwear must be produced (upper sewn to sole) in Indonesia","Bilingual labelling at retail — material composition, size, country of origin","No import licence — standard CBSA documentation","Note: CEPA tariff elimination is phased over 5–15 years, not immediate — current MFN rate applies until phase-out"],
    id_reqs:[],
    ca_market:"Indonesia manufactures footwear for Nike, Adidas, Timberland, and other global brands. The eventual tariff elimination is significant but phased. Canadian footwear retail market is substantial for direct exports once CEPA phases are realised.",
    id_market:"N/A", ca_score:75, id_score:0 },

  { id:"textiles_home", name:"Home Textiles (Towels, Bedding, Curtains)", sector:"Textiles & Apparel", hs:"6302.60.00", direction:"ID→CA",
    ca_mfn:"18%", ca_cepa:"0% (Free, phased over 5–15 years)", ca_saving:"18 percentage points phased over 5–15 years from CEPA entry into force", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["Textile Labelling Act — fibre content label in EN/FR","Care label requirements in both official languages","Rules of origin: cut-and-sew in Indonesia required under CEPA","Standard CBSA commercial documentation"],
    id_reqs:[],
    ca_market:"Indonesia is a significant home textiles exporter. The eventual tariff elimination improves Canadian competitiveness over time. Hudson's Bay, Canadian Tire, and Amazon Canada are realistic buyer channels.",
    id_market:"N/A", ca_score:68, id_score:0 },

  // ── FURNITURE & WOOD ──
  { id:"rattan", name:"Rattan Furniture & Seats", sector:"Furniture & Wood", hs:"9401.69.00", direction:"ID→CA",
    ca_mfn:"9.5%", ca_cepa:"0% (Free, upon entry into force or phased — verify specific HS staging)", ca_saving:"9.5 percentage points upon CEPA entry into force (or phased)", ca_conf:"I",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard import declaration and commercial invoice","CFIA phytosanitary certificate required — rattan is a plant-based material subject to inspection","Consumer Product Safety Act (CCPSA) compliance — stability requirements for seating furniture","Bilingual labelling (EN/FR) — product name, materials, country of origin"],
    id_reqs:[],
    ca_market:"Canada imports approximately CAD $180M in furniture annually. Strong consumer demand for sustainably sourced rattan and natural materials. Indonesia is the world's leading rattan exporter with significant craft and design expertise.",
    id_market:"N/A", ca_score:78, id_score:0 },

  { id:"plywood", name:"Plywood & Engineered Wood", sector:"Furniture & Wood", hs:"4412.31.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA locks in access", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA phytosanitary certificate required for all wood products entering Canada","SVLK (Sistem Verifikasi Legalitas dan Kelestarian) timber legality certificate — mandatory for Indonesian wood product exports","Formaldehyde emission testing to CARB Phase 2 standard required by major Canadian retailers (Home Depot, Rona, Lowes)","National Building Code (NBC) compliance required for structural and construction applications"],
    id_reqs:[],
    ca_market:"Indonesia is the world's largest plywood exporter. SVLK certification and CARB formaldehyde standards are the two practical market access barriers — compliance opens all major Canadian retail and construction supply channels.",
    id_market:"N/A", ca_score:65, id_score:0 },

  { id:"timber", name:"Tropical Hardwood Timber", sector:"Furniture & Wood", hs:"4407.29.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA phytosanitary certificate required","SVLK timber legality certificate mandatory — Canada's imported timber policy effectively requires this","FSC (Forest Stewardship Council) or PEFC certification increasingly required by Canadian retailers and construction buyers","CBSA standard import documentation","CITES documentation if species is listed (e.g. certain Dalbergia/rosewood species are CITES Appendix II)"],
    id_reqs:[],
    ca_market:"Canadian construction and cabinetry sectors import tropical hardwoods. SVLK plus FSC certification is the practical market access combination — without both, major Canadian retail and construction buyers will not source. Key species: merbau, teak, mahogany.",
    id_market:"N/A", ca_score:55, id_score:0 },

  { id:"lumber", name:"Softwood Lumber", sector:"Furniture & Wood", hs:"4407.11.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–5%", id_cepa:"0% (Free, upon entry into force or phased)", id_saving:"Up to 5 percentage points", id_conf:"I",
    ca_reqs:[], id_reqs:["SNI (Indonesian National Standard) certification required for structural lumber applications in construction","Phytosanitary certificate from CFIA required — Indonesia applies phytosanitary measures to all wood imports","Heat treatment or fumigation documentation required under ISPM 15 (international phytosanitary standard for wood packaging)","Ministry of Trade API-U or API-P import registration depending on end use"],
    ca_market:"N/A",
    id_market:"Indonesia's massive infrastructure construction programme (IKN new capital city, toll roads, ports, housing) is driving demand for structural lumber. Canadian Douglas Fir and SPF (Spruce-Pine-Fir) from BC are price-competitive. CEPA opens a major new channel for BC's forest industry.",
    ca_score:0, id_score:72 },

  { id:"handicrafts", name:"Handicrafts & Wood Carvings", sector:"Furniture & Wood", hs:"4420.90.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CITES documentation required if product contains protected wood species — rosewood (Dalbergia spp.) is CITES Appendix II and requires export permits from Indonesia and import permit in Canada","SVLK timber legality certificate for wooden items recommended","Cultural property export permit from Indonesian Ministry of Education and Culture if the item is historically or artistically significant","Standard CBSA commercial documentation"],
    id_reqs:[],
    ca_market:"Indonesian wood carvings from Bali and Jepara are established Canadian import categories. CITES compliance for protected wood species (especially rosewood) is the most significant risk — non-compliance results in CBSA seizure.",
    id_market:"N/A", ca_score:60, id_score:0 },

  // ── RUBBER & PLASTICS ──
  { id:"rubber_natural", name:"Natural Rubber (Smoked Sheets, TSR)", sector:"Rubber & Plastics", hs:"4001.21.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA locks in access", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard commercial documentation — invoice must state grade (RSS 1, RSS 2, TSR 20, etc.), quantity, weight, country of origin","ISO quality grading documentation expected by Canadian industrial buyers","No specific import licence required — treated as industrial material","Substance restriction compliance documentation for end-use in consumer goods manufacturing"],
    id_reqs:[],
    ca_market:"Canada's automotive parts sector and medical device manufacturers are the primary consumers of natural rubber. Indonesia is the world's second-largest natural rubber producer. Supply reliability and consistent quality grading are the key buyer requirements.",
    id_market:"N/A", ca_score:55, id_score:0 },

  { id:"rubber_gloves", name:"Rubber Gloves & Medical PPE", sector:"Rubber & Plastics", hs:"4015.11.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["Health Canada Medical Device Licence (MDL) required — Class I or Class II device classification depending on intended use","ISO 13485 quality management system certification required for medical-grade gloves — this is now a non-negotiable requirement following COVID-era procurement issues","CBSA standard import documentation","ASTM D3578 (examination gloves) or EN 374 (chemical protective gloves) test reports required by Canadian healthcare procurement"],
    id_reqs:[],
    ca_market:"Canada significantly increased medical glove procurement standards following COVID-era supply chain failures. Indonesian manufacturers who achieved ISO 13485 during the pandemic are well-positioned for ongoing Canadian healthcare supply contracts and PPE stockpile procurement.",
    id_market:"N/A", ca_score:68, id_score:0 },

  { id:"tires", name:"Rubber Tires & Tubes", sector:"Rubber & Plastics", hs:"4011.10.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["Transport Canada CMVSS (Canadian Motor Vehicle Safety Standards) Regulation 119 compliance required for tires for use on passenger vehicles — specific load and speed rating markings required","CBSA standard documentation","ISO quality certification (equivalent to DOT standard) required by distributors","Country of origin marking required on tire sidewall"],
    id_reqs:[],
    ca_market:"Indonesia is a significant tire manufacturer (Gajah Tunggal, Multistrada Arah Sarana). Canadian automotive aftermarket is a potential buyer for budget to mid-range tires. Transport Canada CMVSS compliance is the primary technical barrier.",
    id_market:"N/A", ca_score:58, id_score:0 },

  // ── MINERALS & METALS ──
  { id:"nickel", name:"Nickel (Refined Nickel & Ferronickel)", sector:"Minerals & Metals", hs:"7502.10.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA critical minerals provisions strengthen supply chain security and access", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard commercial import declaration","London Metal Exchange (LME) quality specification documentation for refined nickel — purity minimum 99.8% for LME Grade","Supply chain ESG due diligence required — Canadian EV battery manufacturers (Stellantis, Volkswagen, GM plants in Ontario) are implementing rigorous ESG screening for critical mineral suppliers","Transport Canada IMDG Code compliance for bulk metal shipment by sea"],
    id_reqs:[],
    ca_market:"Canada is rapidly building EV battery supply chains in Ontario. Indonesian refined nickel from Sulawesi smelting hubs (HPAL and FeNi) is a strategically critical input. CEPA's dedicated critical minerals provisions are specifically designed to facilitate and secure this supply chain.",
    id_market:"N/A", ca_score:85, id_score:0 },

  { id:"copper", name:"Copper Cathodes & Wire Rod", sector:"Minerals & Metals", hs:"7408.11.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA critical minerals chapter applies", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard import documentation","LME Grade A specification compliance (min 99.99% Cu for cathodes)","Supply chain ESG documentation increasingly required by Canadian manufacturers","No specific import licence required for copper metal — CBSA standard commercial documentation sufficient"],
    id_reqs:[],
    ca_market:"Indonesian copper from Freeport-McMoRan's Grasberg mine (Papua) is among the world's highest grade. Canada's electrical wiring, clean energy, and electronics manufacturing sectors consume significant copper volumes.",
    id_market:"N/A", ca_score:65, id_score:0 },

  { id:"tin", name:"Tin (Refined Tin & Tin Alloys)", sector:"Minerals & Metals", hs:"8001.10.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA critical minerals provisions apply", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard import documentation","LME specification documentation — minimum 99.85% purity for refined tin","Supply chain conflict minerals screening recommended (Bangka-Belitung production areas have been subject to ESG scrutiny)","No specific import licence required"],
    id_reqs:[],
    ca_market:"Indonesia is the world's largest tin exporter. Canadian electronics manufacturing (Toronto/Ottawa tech sector, BC electronics) uses tin extensively for soldering and plating. CEPA critical minerals provisions facilitate this strategic supply chain.",
    id_market:"N/A", ca_score:65, id_score:0 },

  { id:"gold", name:"Gold (Refined Bullion & Doré Bar)", sector:"Minerals & Metals", hs:"7108.12.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA import declaration — all gold imports must be declared","FINTRAC (Financial Transactions and Reports Analysis Centre) reporting obligations — transactions over CAD $10,000 reportable; dealers in precious metals must register","LBMA (London Bullion Market Association) accredited refinery documentation for refined bullion","Anti-money laundering (AML) due diligence required from all Canadian buyers of gold"],
    id_reqs:[],
    ca_market:"Indonesia is a significant gold producer (Freeport-McMoRan Grasberg, Antam). Canadian gold refiners (Royal Canadian Mint, Asahi Refining) and financial institutions are potential buyers. AML due diligence is the primary compliance requirement.",
    id_market:"N/A", ca_score:60, id_score:0 },

  // ── CRITICAL MINERALS ──
  { id:"lithium", name:"Lithium Compounds (Battery Grade)", sector:"Critical Minerals", hs:"2825.20.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–5%", id_cepa:"0% (Free, upon entry into force or phased)", id_saving:"Up to 5 percentage points", id_conf:"I",
    ca_reqs:[], id_reqs:["Ministry of Industry import registration required","BPOM or BSNI product certification for battery-grade lithium compounds","Dangerous goods transport documentation — UN 3264 (corrosive solid) for lithium hydroxide; UN 1432 for lithium phosphide","End-use verification documentation required for battery manufacturing applications"],
    ca_market:"N/A",
    id_market:"Indonesia is building EV battery manufacturing capacity through partnerships with CATL (China), LG Energy Solution (Korea), and Hyundai. Canadian lithium from BC and Ontario spodumene projects is positioned to supply Indonesian battery gigafactories as they come online.",
    ca_score:0, id_score:70 },

  { id:"cobalt", name:"Cobalt & Cobalt Compounds", sector:"Critical Minerals", hs:"2822.00.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0%", id_cepa:"0% (Free)", id_saving:"Already duty-free; CEPA critical minerals provisions provide supply chain security", id_conf:"V",
    ca_reqs:[], id_reqs:["Ministry of Industry import registration","Dangerous goods transport documentation — cobalt compounds classified as hazardous","End-use verification for battery manufacturing applications required","Conflict minerals due diligence documentation (OECD Due Diligence Guidance)"],
    ca_market:"N/A",
    id_market:"Indonesia's EV battery supply chain development creates growing demand for cobalt. Canadian cobalt producers (Glencore Canada, First Cobalt) are positioned to supply Indonesian gigafactories.",
    ca_score:0, id_score:68 },

  // ── PAPER & PACKAGING ──
  { id:"pulp", name:"Wood Pulp (Bleached Kraft)", sector:"Paper & Packaging", hs:"4703.11.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0%", id_cepa:"0% (Free)", id_saving:"Already duty-free; CEPA locks in long-term access", id_conf:"V",
    ca_reqs:[], id_reqs:["Phytosanitary certificate from CFIA required for all wood-derived pulp shipments","Ministry of Trade PI import registration","End-use buyer documentation (paper mill) required","FSC (Forest Stewardship Council) or PEFC certification preferred by large Indonesian paper companies including APP and APRIL"],
    ca_market:"N/A",
    id_market:"Indonesia's paper industry giants (Asia Pulp & Paper/Sinar Mas, APRIL) require significant imported pulp to supplement domestic production. Canadian bleached kraft pulp from BC and Quebec is price-competitive and quality-reliable.",
    ca_score:0, id_score:68 },

  // ── PHARMACEUTICALS ──
  { id:"pharma", name:"Pharmaceutical Products (Generic Medicines)", sector:"Pharmaceuticals", hs:"3004.90.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–5%", id_cepa:"0% (Free, phased over 5–10 years under CEPA)", id_saving:"Up to 5 percentage points as CEPA phases in", id_conf:"I",
    ca_reqs:[], id_reqs:["BPOM (Badan Pengawas Obat dan Makanan) product registration (NIE — Nomor Izin Edar) required before any product can be imported or sold — can take 12–24 months","GMP certificate from Health Canada is required and recognised by BPOM as equivalent","Halal certification (MUI) required for products containing any animal-derived ingredients or excipients","Indonesian language labelling required on all retail packaging — including dosage instructions","Local authorised distributor or agent required to file BPOM registration on behalf of the foreign manufacturer"],
    ca_market:"N/A",
    id_market:"Indonesia is Southeast Asia's largest pharmaceutical market. BPOM registration is the primary market access hurdle — substantial but navigable with proper planning. Canadian generic manufacturers are competitive on quality, GMP compliance, and IP respect.",
    ca_score:0, id_score:65 },

  { id:"medical_devices", name:"Medical Devices & Diagnostic Equipment", sector:"Pharmaceuticals", hs:"9018.90.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–10%", id_cepa:"0% (Free, phased over 5–10 years under CEPA)", id_saving:"Up to 10 percentage points as CEPA phases in", id_conf:"I",
    ca_reqs:[], id_reqs:["BPOM medical device registration (Izin Edar) required before import — classified as Class A/B/C/D based on risk level","Ministry of Health import approval required for certain restricted device categories","ISO 13485 quality management system certification required from the manufacturer","Indonesian licensed distributor or representative required to file BPOM registration","Halal certification required if device contacts bodily fluids or contains animal-derived materials"],
    ca_market:"N/A",
    id_market:"Indonesia's healthcare infrastructure is expanding rapidly, driven by JKN (national health insurance) coverage expansion and new hospital construction. Canadian MedTech (diagnostic imaging, surgical, monitoring equipment) is well-regarded. BPOM registration and local distributor partnerships are the critical first steps.",
    ca_score:0, id_score:72 },

  // ── MACHINERY & EQUIPMENT ──
  { id:"mining_equip", name:"Mining & Drilling Equipment", sector:"Machinery & Equipment", hs:"8430.49.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–5%", id_cepa:"0% (Free, phased over 5–10 years under CEPA)", id_saving:"Up to 5 percentage points", id_conf:"I",
    ca_reqs:[], id_reqs:["API-P (Angka Pengenal Impor Produsen) import licence from Ministry of Trade","Ministry of Industry capital goods import approval","SNI or IEC certification for electrical and safety-critical components","ESDM (Ministry of Energy and Mineral Resources) clearance required at the specific mine site for mining-specific equipment"],
    ca_market:"N/A",
    id_market:"Indonesia's mining boom (nickel, copper, coal, gold) creates substantial and sustained demand for Canadian mining equipment manufacturers. CEPA directly supports this sector.",
    ca_score:0, id_score:80 },

  { id:"agri_equip", name:"Agricultural Machinery & Tractors", sector:"Machinery & Equipment", hs:"8701.91.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"5%", id_cepa:"0% (Free, phased over 5 years under CEPA)", id_saving:"5 percentage points phased over 5 years", id_conf:"I",
    ca_reqs:[], id_reqs:["API-P import licence from Ministry of Trade","Ministry of Agriculture import approval required for agricultural machinery","SNI certification for electrical components of the machinery","After-sales service network establishment recommended by Indonesian buyers — key commercial requirement"],
    ca_market:"N/A",
    id_market:"Indonesia's palm oil, rice paddy, and corn sectors are mechanising rapidly. Canadian agricultural equipment manufacturers (AGCO Canada, CNH Industrial) are competitive. CEPA phases out the 5% tariff within 5 years.",
    ca_score:0, id_score:68 },

  { id:"water_treatment", name:"Water Treatment Systems & Equipment", sector:"Machinery & Equipment", hs:"8421.21.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–5%", id_cepa:"0% (Free, phased over 5 years under CEPA)", id_saving:"Up to 5 percentage points", id_conf:"I",
    ca_reqs:[], id_reqs:["API-P import licence from Ministry of Trade","Ministry of Public Works (PUPR) project approval required for municipal water system projects","SNI certification for electrical and mechanical components","Izin Lingkungan (environmental permit) required for installation at project site"],
    ca_market:"N/A",
    id_market:"Indonesia faces significant water infrastructure challenges — only 72% of the population has access to clean piped water. Canadian water treatment technology (Trojan Technologies UV systems, BWT Canada) is world-class. CEPA specifically supports infrastructure investment.",
    ca_score:0, id_score:70 },

  { id:"construction_equip", name:"Construction & Earthmoving Equipment", sector:"Machinery & Equipment", hs:"8429.51.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–5%", id_cepa:"0% (Free, phased over 5 years under CEPA)", id_saving:"Up to 5 percentage points", id_conf:"I",
    ca_reqs:[], id_reqs:["API-P import licence from Ministry of Trade","Ministry of Industry capital goods registration","SNI certification for electrical components","After-sales service network required by Indonesian equipment buyers — key commercial prerequisite"],
    ca_market:"N/A",
    id_market:"Indonesia's massive infrastructure programme including the IKN new capital city, Trans-Java and Trans-Sumatra toll roads, and new port development drives sustained demand for construction equipment. Canadian manufacturers are competitive.",
    ca_score:0, id_score:72 },

  // ── AUTOMOTIVE ──
  { id:"ev_components", name:"EV Battery Components & Modules", sector:"Automotive", hs:"8507.90.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–10%", id_cepa:"0% (Free, phased over 5–10 years)", id_saving:"Up to 10 percentage points", id_conf:"I",
    ca_reqs:[], id_reqs:["SNI certification for electrical components","API-P import licence from Ministry of Trade","Ministry of Industry approval","TKDN local content requirements apply for government procurement of EVs and components — verify current threshold","AMDAL required for battery manufacturing facility construction"],
    ca_market:"N/A",
    id_market:"Indonesia is positioning itself as a major EV battery manufacturing hub through partnerships with CATL, LG, Hyundai, and Foxconn. Canadian EV component manufacturers are actively targeting this market.",
    ca_score:0, id_score:74 },

  // ── ICT & DIGITAL ──
  { id:"telecom_equip", name:"Telecommunications Equipment", sector:"ICT & Digital", hs:"8517.62.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–10%", id_cepa:"0% (Free, phased over 5–10 years under CEPA)", id_saving:"Up to 10 percentage points", id_conf:"I",
    ca_reqs:[], id_reqs:["SDPPI (Direktorat Jenderal Sumber Daya dan Perangkat Pos dan Informatika) type approval certification required for all radio and telecommunications equipment sold in Indonesia","SNI certification for electrical safety compliance","API-P import licence from Ministry of Trade","TKDN local content requirements may apply for government and state enterprise procurement — verify current thresholds"],
    ca_market:"N/A",
    id_market:"Indonesia's 5G network rollout and digital economy expansion (valued at US$82B in 2023, growing rapidly) create significant demand for telecom infrastructure equipment. Canadian ICT companies are active in the Indonesia market.",
    ca_score:0, id_score:74 },

  { id:"software", name:"Software & IT Services", sector:"ICT & Digital", hs:"N/A", direction:"BOTH",
    ca_mfn:"N/A", ca_cepa:"CEPA digital trade chapter — no customs duties on electronic transmissions; binding commitment by both parties", ca_saving:"CEPA prohibits customs duties on digital products and electronic transmissions between Canada and Indonesia", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"CEPA digital trade provisions apply reciprocally", id_saving:"CEPA improves market access and regulatory transparency for Indonesian tech firms in Canada", id_conf:"V",
    ca_reqs:["No tariffs on digital products or electronic transmissions — binding under CEPA","PIPEDA (Personal Information Protection and Electronic Documents Act) compliance required for handling Canadian personal data","CASL (Canada's Anti-Spam Legislation) compliance required for digital marketing to Canadian users","Provincial consumer protection laws apply depending on nature of service"],
    id_reqs:["OJK (Otoritas Jasa Keuangan) fintech licensing required for financial technology applications","Government Regulation 71/2019: data localisation requirements — certain data categories must be stored on servers in Indonesia","BSSN (National Cyber and Crypto Agency) cybersecurity compliance for critical sector applications","KOMINFO registration required for digital platform providers above specified user number thresholds"],
    ca_market:"Canadian software and SaaS companies are active in Indonesia. CEPA's digital trade chapter, which prohibits customs duties on electronic transmissions, is directly commercially relevant.",
    id_market:"Indonesian tech firms (GoTo, Tokopedia, Traveloka ecosystem) expanding internationally benefit from CEPA's digital trade framework for Canadian market access.",
    ca_score:70, id_score:65 },

  // ── CONSUMER GOODS ──
  { id:"cosmetics", name:"Cosmetics & Personal Care Products", sector:"Consumer Goods", hs:"3304.99.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"10–15%", id_cepa:"0% (Free, phased over 10–15 years under CEPA)", id_saving:"10–15 percentage points phased over 10–15 years", id_conf:"V",
    ca_reqs:[], id_reqs:["BPOM notification system (for cosmetics) — online notification takes 3–6 months and must be completed before first shipment","Halal certification (MUI) is increasingly expected for personal care products — being phased in as mandatory for cosmetics under the Halal Product Assurance Law","Indonesian language labelling required on all retail packaging — ingredients list (INCI format accepted), usage instructions, expiry date","Local authorised agent or distributor required to file the BPOM notification on behalf of the foreign manufacturer"],
    ca_market:"N/A",
    id_market:"Indonesia's beauty and personal care market is growing rapidly driven by a young, aspirational middle class. Canadian natural, organic, and clean beauty brands have strong positioning. BPOM notification and halal certification are the two entry requirements.",
    ca_score:0, id_score:68 },

  // ── SERVICES ──
  { id:"edu_services", name:"Higher Education & Training Services", sector:"Services", hs:"N/A", direction:"BOTH",
    ca_mfn:"N/A", ca_cepa:"CEPA temporary entry and services provisions apply — facilitates entry for Indonesian students and professionals", ca_saving:"CEPA facilitates temporary entry for Indonesian students, professionals, and business persons to Canada", ca_conf:"I",
    id_mfn:"N/A", id_cepa:"CEPA services chapter applies reciprocally", id_saving:"CEPA facilitates temporary entry for Canadian educators, trainers, and education service providers to Indonesia", id_conf:"I",
    ca_reqs:["IRCC (Immigration, Refugees and Citizenship Canada) study permit required for programs over 6 months","Educational Credential Assessment (ECA) required for recognition of Indonesian qualifications in Canada","Provincial professional licensing bodies govern credential recognition by specific field — varies significantly by province","CEPA temporary entry provisions apply for business visitors in the education sector"],
    id_reqs:["DIKTI (Ministry of Higher Education) recognition required for foreign academic credentials","Yayasan (Indonesian foundation) or formal local institutional partnership required to deliver education programs in Indonesia","Izin Tinggal Terbatas (ITAS — limited stay permit) required for Canadian educators on extended assignments","BKPM/OSS-RBA registration required for ongoing educational business operations"],
    ca_market:"Canada is one of the world's top study destinations for Indonesian students — approximately 15,000–20,000 Indonesians study in Canada annually. CEPA's temporary entry provisions streamline professional pathways.",
    id_market:"Canadian universities and colleges are actively expanding in Indonesia through partnerships, articulation agreements, and branch campus models. Strong government-to-government educational cooperation framework.",
    ca_score:80, id_score:70 },

  { id:"consulting", name:"Management Consulting & Advisory Services", sector:"Services", hs:"N/A", direction:"BOTH",
    ca_mfn:"N/A", ca_cepa:"CEPA services chapter — improved market access, transparency, and temporary entry for business persons", ca_saving:"CEPA facilitates temporary entry for Canadian consultants and business visitors to Indonesia under business visitor provisions", ca_conf:"I",
    id_mfn:"N/A", id_cepa:"CEPA services provisions apply reciprocally", id_saving:"CEPA improves transparency and market access for Indonesian professional services firms entering Canada", id_conf:"I",
    ca_reqs:["Izin Tinggal Kunjungan (visit visa) for short-term consulting — up to 60 days, extendable","Izin Tinggal Terbatas (ITAS) for assignments over 60 days — requires sponsor company in Indonesia","BKPM/OSS-RBA registration for ongoing business operations","CEPA business visitor provisions reduce some barriers for short-term engagements"],
    id_reqs:["LMIA (Labour Market Impact Assessment) may be required for extended work assignments in Canada unless covered by CEPA business visitor provisions","Professional body registration varies by province and professional designation (CPA, P.Eng., etc.)","CEPA business visitor provisions apply for short-term consulting engagements under 90 days"],
    ca_market:"Canadian advisory firms in strategy, trade, investment, sustainability, and infrastructure are well-positioned in Indonesia's growing professional services market. MGA specifically operates in this space.",
    id_market:"Indonesian professional services firms have growing opportunities in Canada's multicultural business environment and infrastructure development sectors.",
    ca_score:75, id_score:62 },

  // ── ELECTRICAL MACHINERY & EQUIPMENT (Indonesia's #1 export to Canada — $675M) ──
  { id:"electrical_machinery", name:"Electrical Machinery & Equipment", sector:"ICT & Digital", hs:"8543.70.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA locks in preferential access", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard commercial import documentation","CSA (Canadian Standards Association) or UL certification required for electrical products sold in Canada — mandatory for safety","ISED (Innovation, Science and Economic Development Canada) radio equipment certification if product includes wireless/radio functions","Bilingual labelling (EN/FR) required at retail — product name, safety warnings, manufacturer information"],
    id_reqs:[],
    ca_market:"Electrical machinery and equipment is Indonesia's single largest export to Canada at $675.9M in 2024 — 20.5% of all Canadian imports from Indonesia, growing at 22.9% per year over the past decade. Categories include transformers, insulated wire, circuit boards, electrical components, and home appliances. This is the highest-volume Indonesia–Canada trade flow and should be a priority for Indonesian exporters.",
    id_market:"N/A", ca_score:88, id_score:0 },

  // ── IRON & STEEL (Indonesia is world's 4th largest steel exporter — $28B globally; BOTH directions) ──
  { id:"steel", name:"Iron & Steel Products", sector:"Construction & Infrastructure", hs:"7208.37.00", direction:"BOTH",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free for most steel products under MFN; CEPA locks in access", ca_conf:"V",
    id_mfn:"0–5%", id_cepa:"0% (Free, phased over 5 years)", id_saving:"Up to 5 percentage points as CEPA phases in", id_conf:"I",
    ca_reqs:["CBSA standard commercial import documentation","SIMA (Special Import Measures Act) — anti-dumping and countervailing duties may apply on certain steel products; verify before shipping","CSA standard certification required for structural steel in construction applications","Trade remedy compliance — verify no AD/CVD orders apply to specific HS subheadings"],
    id_reqs:["SNI certification required for structural steel","Ministry of Industry import approval","Anti-dumping investigation compliance — verify current AD status before contracting"],
    ca_market:"Indonesia is the world's 4th largest steel exporter by value ($28B globally in 2024). Indonesian hot-rolled coil, rebar, and stainless steel from Krakatau Steel and downstream nickel-based stainless producers are competitive globally. Canadian construction and manufacturing sectors are potential buyers, subject to SIMA anti-dumping verification.",
    id_market:"Indonesia's massive infrastructure programme (IKN new capital, Trans-Java/Trans-Sumatra toll roads, ports) drives demand for specialty steel. Canadian specialty steel producers are competitive.",
    ca_score:65, id_score:55 },

  // ── AUTOMOTIVE PARTS (Indonesia exports $11B vehicles/parts globally — BOTH directions) ──
  { id:"auto_parts_both", name:"Automotive Parts & Components", sector:"Automotive", hs:"8708.99.00", direction:"BOTH",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free or low MFN; CEPA binds access for Indonesian auto parts exports to Canada", ca_conf:"V",
    id_mfn:"5–15%", id_cepa:"0% (Free, majority phased over 5–10 years — CEPA average benefit confirmed at 8.2 percentage points)", id_saving:"Average 8.2 percentage points on Canadian auto parts exported to Indonesia", id_conf:"V",
    ca_reqs:["CBSA standard import documentation","Transport Canada motor vehicle safety compliance for safety-critical parts","CSA certification for electrical components","Rules of origin: substantial transformation in Indonesia required for CEPA rates"],
    id_reqs:["SNI certification required for safety-critical components (brakes, steering, airbag systems)","Ministry of Industry import approval","API-P import licence","Indonesian licensed distributor typically required for after-market sales"],
    ca_market:"Indonesia's automotive manufacturing sector (Toyota, Honda, Mitsubishi, Daihatsu, Suzuki assembly) produces $11B in vehicles and parts for global export, including to Canada. Indonesian auto parts exporters have growing opportunities in Canadian automotive aftermarket.",
    id_market:"Canada's automotive manufacturing sector (Ontario) requires significant auto parts imports. CEPA's confirmed average 8.2 percentage point tariff reduction is commercially significant for Canadian auto parts exporters.",
    ca_score:62, id_score:72 },

  // ── PAPER & PACKAGING (Indonesia APP/APRIL are global paper giants — BOTH directions) ──
  { id:"paper_both", name:"Paper & Packaging Products", sector:"Paper & Packaging", hs:"4802.55.00", direction:"BOTH",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free; CEPA binds access for Indonesian paper exports", ca_conf:"V",
    id_mfn:"0–5%", id_cepa:"0% (Free, phased over 5 years)", id_saving:"Up to 5 percentage points", id_conf:"I",
    ca_reqs:["CBSA standard import documentation","FSC (Forest Stewardship Council) or PEFC certification preferred — increasingly required by Canadian buyers","No specific import licence required for most paper categories","Phytosanitary certificate for certain packaging materials containing plant-based material"],
    id_reqs:["Standard commercial import documentation","Ministry of Trade PI licence","FSC certification preferred by large Indonesian buyers (APP, APRIL)"],
    ca_market:"Indonesia is home to two of the world's largest pulp and paper companies — Asia Pulp & Paper (APP/Sinar Mas) and APRIL. Indonesian paper, tissue, and packaging products are competitive globally. FSC certification is the key market access requirement for Canadian buyers.",
    id_market:"Indonesia's education, publishing, and packaging sectors create steady demand for paper inputs. CEPA tariff reduction improves Canadian competitiveness vs. Australian and Chinese suppliers.",
    ca_score:65, id_score:55 },

  // ── ADDITIONAL FOOD ──
  { id:"frozen_veg", name:"Frozen Vegetables (Edamame, Green Beans)", sector:"Food Processing", hs:"0710.22.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements","Cold chain documentation (maintained at -18°C)","Pesticide MRL compliance testing","Bilingual labelling","HACCP certification of processing facility"],
    id_reqs:[],
    ca_market:"Canada's frozen vegetable market is strong. Indonesian edamame and green beans are competitive. Cold chain integrity and pesticide compliance are the two key requirements.",
    id_market:"N/A", ca_score:65, id_score:0 },

  { id:"mangoes", name:"Fresh Mangoes", sector:"Tropical Fruits", hs:"0804.50.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA phytosanitary certificate required","Fruit fly (Bactrocera) inspection — Indonesia is a regulated country","Vapour heat treatment may be required as a condition of entry","Bilingual labelling at retail"],
    id_reqs:[],
    ca_market:"Canadian demand for tropical fruits is growing. Indonesian Gedong Gincu and Arumanis varieties are premium products. Pest certification is the primary barrier.",
    id_market:"N/A", ca_score:55, id_score:0 },

  { id:"pineapple", name:"Fresh & Canned Pineapple", sector:"Tropical Fruits", hs:"0804.30.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA phytosanitary inspection","Fruit fly certification for fresh product","HACCP for processed/canned pineapple","Bilingual labelling"],
    id_reqs:[],
    ca_market:"Processed pineapple (canned, juice) faces lower phytosanitary hurdles than fresh. Strong demand in Canadian food manufacturing.",
    id_market:"N/A", ca_score:60, id_score:0 },

  { id:"corn", name:"Corn (Maize) & Corn Products", sector:"Grains & Agriculture", hs:"1005.90.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–5%", id_cepa:"0% (Free, upon entry into force)", id_saving:"Up to 5 percentage points", id_conf:"I",
    ca_reqs:[],
    id_reqs:["BPOM or Ministry of Agriculture import approval","Phytosanitary certificate","GMO declaration required","PI import licence"],
    ca_market:"N/A",
    id_market:"Indonesia's poultry and livestock feed sector consumes significant corn imports. Canadian corn is competitive. Indonesia periodically runs supply deficits requiring imports.",
    ca_score:0, id_score:60 },

  { id:"canola_meal", name:"Canola Meal (Animal Feed)", sector:"Grains & Agriculture", hs:"2306.41.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0%", id_cepa:"0% (Free)", id_saving:"Already duty-free; CEPA binds access", id_conf:"V",
    ca_reqs:[],
    id_reqs:["Ministry of Agriculture feed import permit","Quality certification","Phytosanitary certificate from CFIA","GMO status declaration"],
    ca_market:"N/A",
    id_market:"Indonesia's poultry and aquaculture sectors are large consumers of protein meal. Canadian canola meal is competitive on quality and price.",
    ca_score:0, id_score:68 },

  { id:"battery_storage", name:"Battery Energy Storage Systems", sector:"Energy", hs:"8507.60.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"5–10%", id_cepa:"0% (Free, phased over 10 years)", id_saving:"5–10 percentage points", id_conf:"I",
    ca_reqs:[],
    id_reqs:["SNI certification for electrical equipment","API-P import licence","Ministry of Energy project approval","AMDAL for large-scale grid installations"],
    ca_market:"N/A",
    id_market:"Indonesia's energy transition requires grid-scale and distributed battery storage. Canadian clean energy companies are active in this sector.",
    ca_score:0, id_score:68 },

  { id:"computers", name:"Computers & Laptops", sector:"ICT & Digital", hs:"8471.30.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0%", id_cepa:"0% (Free)", id_saving:"Already duty-free; CEPA binds access", id_conf:"V",
    ca_reqs:[],
    id_reqs:["SDPPI type approval certification","SNI for electrical safety","API-P import licence"],
    ca_market:"N/A",
    id_market:"Indonesia's digital economy growth drives strong demand for computing equipment. Canadian brands are competitive in the premium segment.",
    ca_score:0, id_score:62 },

  { id:"vitamins", name:"Vitamins & Nutritional Supplements", sector:"Pharmaceuticals", hs:"2106.10.00", direction:"CA→ID",
    ca_mfn:"N/A", id_mfn:"0–5%", id_cepa:"0% (Free, phased over 5–10 years)", id_saving:"Up to 5 percentage points", id_conf:"I",
    ca_reqs:[],
    id_reqs:["BPOM registration required (supplement classification)","Halal certification (MUI) if animal-derived ingredients","Indonesian language labelling","Shelf life compliance — minimum 2/3 remaining upon arrival"],
    ca_market:"N/A",
    id_market:"Indonesia's health supplement market is one of Southeast Asia's fastest growing. Canadian brands are well-regarded for quality. BPOM registration (6–12 months) is the primary entry requirement.",
    ca_score:0, id_score:65 },

  // ── ARTS & CRAFTS ──
  { id:"batik_art", name:"Batik Art & Wall Décor", sector:"Arts & Crafts", hs:"9701.10.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard import documentation","Cultural property export permit if historically significant","CITES if dye materials include protected species"],
    id_reqs:[],
    ca_market:"Growing Canadian market for artisan and cultural décor. Indonesian batik art commands strong premiums in gallery and online channels. UNESCO recognition supports premium positioning.",
    id_market:"N/A", ca_score:65, id_score:0 },

  { id:"squid", name:"Squid & Octopus (Frozen)", sector:"Seafood", hs:"0307.43.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA import licence","Cold chain documentation","HACCP certification","Bilingual labelling"],
    id_reqs:[],
    ca_market:"Canadian foodservice and ethnic retail sectors are buyers for frozen squid and octopus. Indonesia is a significant producer from Sulawesi and Eastern Indonesia.",
    id_market:"N/A", ca_score:65, id_score:0 },

  { id:"palm_olein", name:"Refined Palm Olein (RBD)", sector:"Vegetable Oils", hs:"1511.90.10", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA import licence for refined oils","Health Canada food standards compliance","RSPO supply chain certification preferred by Canadian manufacturers"],
    id_reqs:[],
    ca_market:"Refined palm olein is used in snack food, margarine, and frying oils. Indonesia is the world's largest exporter. RSPO certification is the commercial differentiator.",
    id_market:"N/A", ca_score:60, id_score:0 },

  { id:"coffee_processed", name:"Roasted Coffee & Coffee Extracts", sector:"Coffee & Beverages", hs:"0901.21.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements","Bilingual labelling (EN/FR)","Roasting date and best-before labelling","Organic or Fair Trade certification for premium segment"],
    id_reqs:[],
    ca_market:"Branded Indonesian roasted coffees (Toraja, Mandheling) have niche positioning in Canadian specialty retail. Growing direct-to-consumer e-commerce channel.",
    id_market:"N/A", ca_score:65, id_score:0 },

  { id:"dragon_fruit", name:"Dragon Fruit (Pitaya)", sector:"Tropical Fruits", hs:"0810.90.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA phytosanitary certificate","Fruit fly inspection","Cold chain documentation","Bilingual labelling at retail"],
    id_reqs:[],
    ca_market:"Rapidly growing demand in Canada for exotic superfruits. Indonesian dragon fruit commands premium pricing. Air freight logistics are the main challenge.",
    id_market:"N/A", ca_score:62, id_score:0 },

  { id:"cassava", name:"Cassava Starch & Tapioca", sector:"Tropical Fruits", hs:"1108.14.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food import requirements","Health Canada food additive approval","Moisture and contaminant testing"],
    id_reqs:[],
    ca_market:"Used in gluten-free food manufacturing, baby food, and biodegradable packaging. Growing Canadian health food sector creates demand.",
    id_market:"N/A", ca_score:58, id_score:0 },

  // ── ADDITIONAL TEXTILES ──
  { id:"garments_synthetic", name:"Synthetic & Activewear Garments", sector:"Textiles & Apparel", hs:"6110.30.00", direction:"ID→CA",
    ca_mfn:"18%", ca_cepa:"0% (Free, phased over 5–15 years)", ca_saving:"18 percentage points phased over 5–15 years", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["Textile Labelling Act compliance (EN/FR)","Rules of origin: cut-and-sew in Indonesia required","Standard CBSA documentation"],
    id_reqs:[],
    ca_market:"Sportswear, activewear, and fast fashion segments. Indonesian manufacturers produce competitively for global brands. CEPA tariff elimination (phased) opens Canadian market access.",
    id_market:"N/A", ca_score:70, id_score:0 },

  // ── ADDITIONAL MINERALS ──
  { id:"bauxite_alumina", name:"Bauxite & Alumina", sector:"Minerals & Metals", hs:"2606.00.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard documentation for industrial minerals","Transport Canada bulk cargo regulations"],
    id_reqs:[],
    ca_market:"Indonesia imposed export restrictions on unprocessed bauxite in 2023. Processed alumina is the viable flow. Canada's aluminum smelting sector is a potential buyer.",
    id_market:"N/A", ca_score:50, id_score:0 },

  { id:"furniture_general", name:"General Wood & Metal Furniture", sector:"Furniture & Wood", hs:"9403.60.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA phytosanitary certificate for wood furniture","SVLK certificate for tropical wood","CCPSA compliance for consumer furniture","Bilingual labelling"],
    id_reqs:[],
    ca_market:"Indonesia is a significant furniture exporter. Canadian home furnishing retail (Wayfair, IKEA suppliers) represents a strong market.",
    id_market:"N/A", ca_score:68, id_score:0 },

  // ── ADDITIONAL RUBBER ──
  { id:"ceramics", name:"Ceramics & Tableware", sector:"Consumer Goods", hs:"6912.00.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["Health Canada lead and cadmium migration limits for ceramic tableware","Consumer Product Safety Act (CCPSA) compliance","Bilingual labelling"],
    id_reqs:[],
    ca_market:"Indonesian ceramics from Lombok and Java have established export markets. Lead/cadmium testing is the primary regulatory requirement.",
    id_market:"N/A", ca_score:58, id_score:0 },

  { id:"toys", name:"Toys & Children's Products", sector:"Consumer Goods", hs:"9503.00.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["Consumer Product Safety Act (CCPSA) — toys must meet Canadian safety standards","Canada's Toys Regulations (SOR/2011-17) — phthalates, heavy metals, small parts","Bilingual labelling (EN/FR) mandatory","Age grading and hazard warnings required"],
    id_reqs:[],
    ca_market:"Indonesia manufactures toys for global brands. Canadian toy retail and e-commerce channels are accessible. Safety certification is the primary compliance requirement.",
    id_market:"N/A", ca_score:60, id_score:0 },

  { id:"jewellery", name:"Gold & Silver Jewellery", sector:"Consumer Goods", hs:"7113.19.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard documentation — invoice must state metal purity, stone type, country of origin","FINTRAC reporting obligations for high-value transactions over CAD $10,000","Gemstone country of origin documentation recommended"],
    id_reqs:[],
    ca_market:"Indonesian gold and silver jewellery (Bali filigree, Javanese gold work) have established niches in Canadian ethnic and artisan markets.",
    id_market:"N/A", ca_score:62, id_score:0 },

  // ── ADDITIONAL GRAINS ──
  { id:"musical_instruments", name:"Traditional Musical Instruments (Gamelan, etc.)", sector:"Arts & Crafts", hs:"9205.90.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CBSA standard documentation","CITES documentation if exotic wood or animal materials are used","Cultural property regulations may apply for antique instruments"],
    id_reqs:[],
    ca_market:"Canadian arts institutions, universities, and multicultural communities are buyers for Indonesian traditional instruments. Niche but growing market.",
    id_market:"N/A", ca_score:50, id_score:0 },

  // ── ADDITIONAL SEAFOOD ──
  { id:"fish_meal", name:"Fish Meal & Fish Oil", sector:"Seafood", hs:"2301.20.00", direction:"ID→CA",
    ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"Already duty-free", ca_conf:"V",
    id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V",
    ca_reqs:["CFIA food/feed import requirements","Phytosanitary certificate","Quality specification testing (protein content, moisture)","Veterinary certificate for animal feed use"],
    id_reqs:[],
    ca_market:"Canadian aquaculture and livestock sectors use fish meal as feed. Indonesian fish meal from sardine and anchovy processing is competitively priced.",
    id_market:"N/A", ca_score:55, id_score:0 },

];

// ── DATA LOGIC ────────────────────────────────────────────────────────────────
// When origin=CA, mode=export → exporting TO Indonesia → show id_* (what Indonesia requires to let goods in)
// When origin=CA, mode=import → importing FROM Indonesia → show ca_* (what Canada requires to let goods in)
// When origin=ID, mode=export → exporting TO Canada → show ca_* (what Canada requires to let goods in)
// When origin=ID, mode=import → importing FROM Canada → show id_* (what Indonesia requires to let goods in)

function showIdSide(origin, mode) {
  return (origin === "CA" && mode === "export") || (origin === "ID" && mode === "import");
}

function getProductData(product, origin, mode) {
  if (!product || !origin || !mode) return null;
  const idSide = showIdSide(origin, mode);
  return idSide
    ? { mfn:product.id_mfn, cepa:product.id_cepa, saving:product.id_saving, conf:product.id_conf, reqs:product.id_reqs, market:product.id_market, score:product.id_score, regsTitle:"Indonesian Import Requirements", marketTitle:"Indonesian Market Signal", tariffTitle:"Indonesia's tariff on this product" }
    : { mfn:product.ca_mfn, cepa:product.ca_cepa, saving:product.ca_saving, conf:product.ca_conf, reqs:product.ca_reqs, market:product.ca_market, score:product.ca_score, regsTitle:"Canadian Import Requirements", marketTitle:"Canadian Market Signal", tariffTitle:"Canada's tariff on this product" };
}

function filterByFlow(products, origin, mode) {
  if (!origin || !mode) return products;
  return products.filter(p => {
    if (origin === "CA" && mode === "export") return p.direction === "CA→ID" || p.direction === "BOTH";
    if (origin === "CA" && mode === "import") return p.direction === "ID→CA" || p.direction === "BOTH";
    if (origin === "ID" && mode === "export") return p.direction === "ID→CA" || p.direction === "BOTH";
    if (origin === "ID" && mode === "import") return p.direction === "CA→ID" || p.direction === "BOTH";
    return true;
  });
}

function searchProducts(q, products, origin, mode) {
  if (!q || q.length < 2) return [];
  const ql = q.toLowerCase();
  return filterByFlow(products, origin, mode).filter(p =>
    p.name.toLowerCase().includes(ql) || p.sector.toLowerCase().includes(ql) || p.hs.includes(ql)
  );
}

function popularProducts(products, origin, mode) {
  const idSide = showIdSide(origin, mode);
  return filterByFlow(products, origin, mode)
    .filter(p => (idSide ? p.id_score : p.ca_score) >= 70)
    .slice(0, 12);
}

function sectorProds(s, products, origin, mode) {
  return filterByFlow(products, origin, mode).filter(p => p.sector === s);
}

const SECTORS = [...new Set(INITIAL_PRODUCTS.map(p => p.sector))].sort();

// ── ADMIN PANEL ───────────────────────────────────────────────────────────────
function AdminPanel({ products, onUpdate, onClose }) {
  const [tab, setTab] = useState("list");
  const [editId, setEditId] = useState(null);
  const [editData, setEditData] = useState(null);
  const [msg, setMsg] = useState("");
  const blankProd = { id:"", name:"", sector:"", hs:"", direction:"ID→CA", ca_mfn:"0%", ca_cepa:"0% (Free)", ca_saving:"", ca_conf:"V", id_mfn:"N/A", id_cepa:"N/A", id_saving:"N/A", id_conf:"V", ca_reqs:[""], id_reqs:[""], ca_market:"N/A", id_market:"N/A", ca_score:50, id_score:50 };
  const [newProd, setNewProd] = useState({ ...blankProd });

  const notify = m => { setMsg(m); setTimeout(() => setMsg(""), 7000); };
  const startEdit = p => { setEditId(p.id); setEditData(JSON.parse(JSON.stringify(p))); setTab("edit"); };
  const saveEdit = () => { onUpdate(products.map(p => p.id === editId ? editData : p)); notify("✓ Saved (session only). Note your changes and send to MGA to make permanent."); setTab("list"); };
  const delProd = id => { if (window.confirm("Delete this product?")) onUpdate(products.filter(p => p.id !== id)); };
  const addProd = () => {
    if (!newProd.id || !newProd.name) { alert("ID and Name are required."); return; }
    if (products.find(p => p.id === newProd.id)) { alert("ID already exists."); return; }
    const prod = { ...newProd, ca_reqs:newProd.ca_reqs.filter(r=>r.trim()), id_reqs:newProd.id_reqs.filter(r=>r.trim()), ca_score:Number(newProd.ca_score), id_score:Number(newProd.id_score) };
    onUpdate([...products, prod]); notify("✓ Product added (session only)."); setNewProd({...blankProd}); setTab("list");
  };

  const FG = ({label, children}) => <div style={{marginBottom:"0.65rem"}}><div style={{fontFamily:"'DM Mono',monospace",fontSize:"0.52rem",letterSpacing:"0.12em",textTransform:"uppercase",color:C.muted,marginBottom:"0.2rem"}}>{label}</div>{children}</div>;
  const inp = (val, onChange, ph="", mono=false) => <input value={val} onChange={e=>onChange(e.target.value)} placeholder={ph} style={{width:"100%",padding:"0.4rem 0.55rem",fontFamily:mono?"'DM Mono',monospace":"'DM Sans',sans-serif",fontSize:"0.75rem",border:`1px solid ${C.border}`,outline:"none",boxSizing:"border-box"}}/>;
  const sel = (val, onChange, opts) => <select value={val} onChange={e=>onChange(e.target.value)} style={{width:"100%",padding:"0.4rem",fontFamily:"'DM Sans',sans-serif",fontSize:"0.75rem",border:`1px solid ${C.border}`,outline:"none"}}>{opts.map(o=><option key={o} value={o}>{o}</option>)}</select>;
  const ReqList = ({reqs, onChange}) => <div>{reqs.map((r,i)=><div key={i} style={{display:"flex",gap:"0.35rem",marginBottom:"0.3rem"}}><input value={r} onChange={e=>{const n=[...reqs];n[i]=e.target.value;onChange(n);}} placeholder={`Requirement ${i+1}`} style={{flex:1,padding:"0.35rem 0.55rem",fontFamily:"'DM Sans',sans-serif",fontSize:"0.74rem",border:`1px solid ${C.border}`,outline:"none"}}/><button onClick={()=>onChange(reqs.filter((_,j)=>j!==i))} style={{background:C.red,color:"#fff",border:"none",padding:"0 0.55rem",cursor:"pointer"}}>×</button></div>)}<button onClick={()=>onChange([...reqs,""])} style={{background:"transparent",border:`1px dashed ${C.border}`,padding:"0.28rem 0.65rem",fontFamily:"'DM Mono',monospace",fontSize:"0.56rem",cursor:"pointer",color:C.muted,width:"100%",marginTop:"0.2rem"}}>+ Add requirement</button></div>;

  const EditForm = ({data, setData, onSave, onCancel}) => (
    <div>
      <div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:"0.6rem",marginBottom:"0.75rem"}}>
        <FG label="Product Name">{inp(data.name, v=>setData({...data,name:v}))}</FG>
        <FG label="HS Code">{inp(data.hs, v=>setData({...data,hs:v}), "0000.00.00", true)}</FG>
        <FG label="Sector">{inp(data.sector, v=>setData({...data,sector:v}))}</FG>
        <FG label="Direction">{sel(data.direction, v=>setData({...data,direction:v}), ["ID→CA","CA→ID","BOTH"])}</FG>
      </div>
      <div style={{background:"rgba(61,189,184,0.05)",padding:"0.75rem",marginBottom:"0.65rem",borderLeft:`2px solid ${C.teal}`}}>
        <div style={{fontFamily:"'DM Mono',monospace",fontSize:"0.52rem",color:C.teal,letterSpacing:"0.1em",textTransform:"uppercase",marginBottom:"0.5rem"}}>Canadian Import Data — goods entering Canada from Indonesia</div>
        <div style={{display:"grid",gridTemplateColumns:"1fr 1fr 1fr",gap:"0.45rem"}}>
          <FG label="MFN Rate">{inp(data.ca_mfn, v=>setData({...data,ca_mfn:v}), "e.g. 18%", true)}</FG>
          <FG label="CEPA Rate">{inp(data.ca_cepa, v=>setData({...data,ca_cepa:v}), "e.g. 0% (Free)", true)}</FG>
          <FG label="Confidence">{sel(data.ca_conf, v=>setData({...data,ca_conf:v}), ["V","I"])}</FG>
        </div>
        <FG label="CEPA Saving Note">{inp(data.ca_saving, v=>setData({...data,ca_saving:v}))}</FG>
        <FG label="Canadian Market Signal"><textarea value={data.ca_market} onChange={e=>setData({...data,ca_market:e.target.value})} rows={2} style={{width:"100%",padding:"0.4rem",fontFamily:"'DM Sans',sans-serif",fontSize:"0.74rem",border:`1px solid ${C.border}`,outline:"none",resize:"vertical",boxSizing:"border-box"}}/></FG>
        <FG label={`Market Score: ${data.ca_score}/100`}><input type="range" min="0" max="100" value={data.ca_score} onChange={e=>setData({...data,ca_score:Number(e.target.value)})} style={{width:"100%"}}/></FG>
        <FG label="Canadian Import Requirements (what Canada requires to let goods in)"><ReqList reqs={data.ca_reqs} onChange={v=>setData({...data,ca_reqs:v})}/></FG>
      </div>
      <div style={{background:"rgba(212,134,26,0.05)",padding:"0.75rem",marginBottom:"0.65rem",borderLeft:`2px solid ${C.amber}`}}>
        <div style={{fontFamily:"'DM Mono',monospace",fontSize:"0.52rem",color:C.amber,letterSpacing:"0.1em",textTransform:"uppercase",marginBottom:"0.5rem"}}>Indonesian Import Data — goods entering Indonesia from Canada</div>
        <div style={{display:"grid",gridTemplateColumns:"1fr 1fr 1fr",gap:"0.45rem"}}>
          <FG label="MFN Rate">{inp(data.id_mfn, v=>setData({...data,id_mfn:v}), "e.g. 5%", true)}</FG>
          <FG label="CEPA Rate">{inp(data.id_cepa, v=>setData({...data,id_cepa:v}), "e.g. 0% (Free)", true)}</FG>
          <FG label="Confidence">{sel(data.id_conf, v=>setData({...data,id_conf:v}), ["V","I"])}</FG>
        </div>
        <FG label="CEPA Saving Note">{inp(data.id_saving, v=>setData({...data,id_saving:v}))}</FG>
        <FG label="Indonesian Market Signal"><textarea value={data.id_market} onChange={e=>setData({...data,id_market:e.target.value})} rows={2} style={{width:"100%",padding:"0.4rem",fontFamily:"'DM Sans',sans-serif",fontSize:"0.74rem",border:`1px solid ${C.border}`,outline:"none",resize:"vertical",boxSizing:"border-box"}}/></FG>
        <FG label={`Market Score: ${data.id_score}/100`}><input type="range" min="0" max="100" value={data.id_score} onChange={e=>setData({...data,id_score:Number(e.target.value)})} style={{width:"100%"}}/></FG>
        <FG label="Indonesian Import Requirements (what Indonesia requires to let goods in)"><ReqList reqs={data.id_reqs} onChange={v=>setData({...data,id_reqs:v})}/></FG>
      </div>
      <div style={{display:"flex",gap:"0.5rem"}}>
        <button onClick={onSave} style={{background:C.teal,color:"#fff",border:"none",padding:"0.58rem 1.2rem",fontFamily:"'DM Mono',monospace",fontSize:"0.6rem",letterSpacing:"0.1em",textTransform:"uppercase",cursor:"pointer"}}>Save</button>
        <button onClick={onCancel} style={{background:"transparent",border:`1px solid ${C.border}`,padding:"0.58rem 1.2rem",fontFamily:"'DM Mono',monospace",fontSize:"0.6rem",letterSpacing:"0.1em",textTransform:"uppercase",cursor:"pointer",color:C.muted}}>Cancel</button>
      </div>
    </div>
  );

  return (
    <div style={{position:"fixed",inset:0,background:"rgba(0,0,0,0.65)",zIndex:1000,display:"flex",alignItems:"flex-start",justifyContent:"center",overflowY:"auto",padding:"1.5rem"}}>
      <div style={{background:C.white,width:"100%",maxWidth:"780px",boxShadow:"0 20px 60px rgba(0,0,0,0.3)"}}>
        <div style={{background:C.navy,padding:"1rem 1.5rem",display:"flex",justifyContent:"space-between",alignItems:"center"}}>
          <div><div style={{fontFamily:"'DM Mono',monospace",fontSize:"0.68rem",fontWeight:600,letterSpacing:"0.1em",color:"#fff"}}>⚙ MGA Admin Panel</div><div style={{fontFamily:"'DM Mono',monospace",fontSize:"0.52rem",color:"rgba(255,255,255,0.4)",marginTop:"0.2rem"}}>{products.length} products · session only</div></div>
          <button onClick={onClose} style={{background:"transparent",border:"1px solid rgba(255,255,255,0.2)",color:"rgba(255,255,255,0.7)",fontFamily:"'DM Mono',monospace",fontSize:"0.58rem",padding:"0.28rem 0.7rem",cursor:"pointer"}}>Close ×</button>
        </div>
        <div style={{background:"rgba(212,134,26,0.1)",borderBottom:`1px solid rgba(212,134,26,0.25)`,padding:"0.5rem 1.5rem",fontSize:"0.7rem",color:C.amber}}>⚠ Changes are <strong>session-only</strong> and reset on close. Note your edits and send to MGA to make them permanent in the code.</div>
        {msg && <div style={{background:"rgba(42,157,111,0.1)",borderBottom:`1px solid rgba(42,157,111,0.25)`,padding:"0.5rem 1.5rem",fontSize:"0.7rem",color:C.green}}>{msg}</div>}
        <div style={{display:"flex",borderBottom:`1px solid ${C.border}`}}>
          {[["list","📋 Products"],["add","➕ Add New"]].map(([v,label])=>(
            <button key={v} onClick={()=>{setTab(v);setEditId(null);}} style={{padding:"0.58rem 1.2rem",fontFamily:"'DM Mono',monospace",fontSize:"0.58rem",letterSpacing:"0.08em",border:"none",borderBottom:tab===v?`2px solid ${C.teal}`:"2px solid transparent",cursor:"pointer",background:"transparent",color:tab===v?C.teal:C.muted}}>{label}</button>
          ))}
          {tab==="edit"&&<div style={{padding:"0.58rem 1.2rem",fontFamily:"'DM Mono',monospace",fontSize:"0.58rem",letterSpacing:"0.08em",borderBottom:`2px solid ${C.teal}`,color:C.teal}}>✏ Editing</div>}
        </div>
        <div style={{padding:"1.2rem 1.5rem"}}>
          {tab==="list"&&<div style={{display:"flex",flexDirection:"column",gap:"1px",background:C.border}}>{products.map(p=><div key={p.id} style={{background:C.white,display:"flex",justifyContent:"space-between",alignItems:"center",padding:"0.58rem 0.9rem"}}><div><div style={{fontSize:"0.82rem",fontWeight:600,color:C.navy}}>{p.name}</div><div style={{fontFamily:"'DM Mono',monospace",fontSize:"0.55rem",color:C.muted}}>{p.hs!=="N/A"?`HS ${p.hs}`:"Services"} · {p.sector} · {p.direction}</div></div><div style={{display:"flex",gap:"0.35rem"}}><button onClick={()=>startEdit(p)} style={{background:C.teal,color:"#fff",border:"none",padding:"0.27rem 0.6rem",fontFamily:"'DM Mono',monospace",fontSize:"0.55rem",cursor:"pointer"}}>Edit</button><button onClick={()=>delProd(p.id)} style={{background:C.red,color:"#fff",border:"none",padding:"0.27rem 0.6rem",fontFamily:"'DM Mono',monospace",fontSize:"0.55rem",cursor:"pointer"}}>Del</button></div></div>)}</div>}
          {tab==="edit"&&editData&&<EditForm data={editData} setData={setEditData} onSave={saveEdit} onCancel={()=>{setTab("list");setEditId(null);}}/>}
          {tab==="add"&&<div><div style={{marginBottom:"0.6rem",fontFamily:"'DM Mono',monospace",fontSize:"0.56rem",color:C.muted}}>ID must be unique with no spaces (use underscores). Only fill in the side(s) relevant to the direction.</div><div style={{display:"grid",gridTemplateColumns:"1fr 1fr",gap:"0.6rem",marginBottom:"0.65rem"}}><FG label="Unique ID">{inp(newProd.id, v=>setNewProd({...newProd,id:v.replace(/\s/g,"_")}), "e.g. palm_kernel_oil", true)}</FG><FG label="Direction">{sel(newProd.direction, v=>setNewProd({...newProd,direction:v}), ["ID→CA","CA→ID","BOTH"])}</FG></div><EditForm data={newProd} setData={setNewProd} onSave={addProd} onCancel={()=>setTab("list")}/></div>}
        </div>
      </div>
    </div>
  );
}

// ── MAIN APP ──────────────────────────────────────────────────────────────────
export default function App() {
  const [products, setProducts] = useState(INITIAL_PRODUCTS);
  const [origin, setOrigin]     = useState(null);   // "CA" | "ID"
  const [mode, setMode]         = useState(null);   // "export" | "import"
  const [query, setQuery]       = useState("");
  const [selected, setSelected] = useState(null);
  const [sector, setSector]     = useState(null);
  const [view, setView]         = useState("search");
  const [adminOpen, setAdminOpen]   = useState(false);
  const [adminInput, setAdminInput] = useState(false);
  const [adminPw, setAdminPw]       = useState("");
  const [pwError, setPwError]       = useState(false);

  const isCA = origin === "CA";
  const destName = showIdSide(origin, mode) ? "Indonesia" : "Canada";
  const homeName = isCA ? "Canada" : "Indonesia";
  const modeLabel = mode === "export" ? `Exporting to ${destName}` : mode === "import" ? `Importing from ${destName}` : "";

  const filtered  = useMemo(() => filterByFlow(products, origin, mode), [products, origin, mode]);
  const results   = useMemo(() => searchProducts(query, products, origin, mode), [query, products, origin, mode]);
  const popular   = useMemo(() => mode ? popularProducts(products, origin, mode) : [], [products, origin, mode]);
  const visSectors = useMemo(() => SECTORS.filter(s => sectorProds(s, products, origin, mode).length > 0), [products, origin, mode]);
  const pData     = useMemo(() => selected ? getProductData(selected, origin, mode) : null, [selected, origin, mode]);

  // ── BROWSER BACK BUTTON — intercept so it navigates within the tool ──────────
  // Push a history state whenever the user moves to a new step
  useEffect(() => {
    if (selected)      { window.history.pushState({ step:"product" }, ""); }
    else if (mode)     { window.history.pushState({ step:"search" }, ""); }
    else if (origin)   { window.history.pushState({ step:"mode" }, ""); }
  }, [origin, mode, selected]);

  useEffect(() => {
    const onPop = () => {
      if (selected)         { setSelected(null); }
      else if (mode)        { setMode(null); setQuery(""); setSector(null); }
      else if (origin)      { setOrigin(null); }
    };
    window.addEventListener("popstate", onPop);
    return () => window.removeEventListener("popstate", onPop);
  }, [selected, mode, origin]);

  function reset()     { setOrigin(null); setMode(null); setSelected(null); setQuery(""); setSector(null); setView("search"); }
  function resetMode() { setMode(null); setSelected(null); setQuery(""); setSector(null); setView("search"); }

  function tryAdmin() {
    if (adminPw === ADMIN_PW) { setAdminOpen(true); setAdminInput(false); setPwError(false); setAdminPw(""); }
    else { setPwError(true); setAdminPw(""); }
  }

  const ProdRow = ({ p }) => (
    <button onClick={() => setSelected(p)}
      style={{ background:C.white, border:"none", borderBottom:`1px solid ${C.borderLight}`, padding:"0.9rem 1.2rem", cursor:"pointer", textAlign:"left", display:"flex", justifyContent:"space-between", alignItems:"center", width:"100%" }}
      onMouseEnter={e=>e.currentTarget.style.background=C.light} onMouseLeave={e=>e.currentTarget.style.background=C.white}>
      <div>
        <div style={{ fontFamily:"'Inter',sans-serif", fontWeight:500, fontSize:"0.87rem", color:C.navy, marginBottom:"0.15rem" }}>{p.name}</div>
        <div style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.58rem", color:C.muted }}>{p.hs!=="N/A"?`HS ${p.hs}`:"Services"} · {p.sector}</div>
      </div>
      <span style={{ color:C.gold, fontSize:"1rem", marginLeft:"0.5rem", fontWeight:300 }}>→</span>
    </button>
  );

  const navBtn = { background:"transparent", border:`1px solid rgba(255,255,255,0.2)`, color:"rgba(255,255,255,0.65)", fontFamily:"'DM Mono',monospace", fontSize:"0.56rem", letterSpacing:"0.06em", padding:"0.28rem 0.68rem", cursor:"pointer" };

  return (
    <div style={{ fontFamily:"'Inter',sans-serif", background:C.cream, minHeight:"100vh", color:C.navy }}>
      <style>{`@import url('${FONT_LINK}'); *{box-sizing:border-box;} h1,h2,h3{font-family:'Cormorant Garamond',serif;}`}</style>

      {adminOpen && <AdminPanel products={products} onUpdate={setProducts} onClose={() => setAdminOpen(false)}/>}

      {/* Admin password modal */}
      {adminInput && (
        <div style={{ position:"fixed", inset:0, background:"rgba(0,0,0,0.6)", zIndex:999, display:"flex", alignItems:"center", justifyContent:"center" }}>
          <div style={{ background:C.white, padding:"2rem", width:"320px", boxShadow:"0 10px 40px rgba(0,0,0,0.25)" }}>
            <div style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.65rem", letterSpacing:"0.12em", textTransform:"uppercase", color:C.gold, marginBottom:"1rem" }}>Admin Access</div>
            <input type="password" value={adminPw} onChange={e=>{setAdminPw(e.target.value);setPwError(false);}} onKeyDown={e=>e.key==="Enter"&&tryAdmin()} placeholder="Enter password"
              style={{ width:"100%", padding:"0.65rem", fontFamily:"'DM Mono',monospace", fontSize:"0.85rem", border:`1.5px solid ${pwError?C.red:C.border}`, outline:"none", marginBottom:"0.5rem" }}/>
            {pwError && <div style={{ fontSize:"0.7rem", color:C.red, marginBottom:"0.5rem" }}>Incorrect password.</div>}
            <div style={{ display:"flex", gap:"0.5rem" }}>
              <button onClick={tryAdmin} style={{ flex:1, background:C.navy, color:"#fff", border:"none", padding:"0.6rem", fontFamily:"'DM Mono',monospace", fontSize:"0.62rem", letterSpacing:"0.1em", cursor:"pointer" }}>Enter</button>
              <button onClick={()=>{setAdminInput(false);setPwError(false);setAdminPw("");}} style={{ flex:1, background:"transparent", border:`1px solid ${C.border}`, padding:"0.6rem", fontFamily:"'DM Mono',monospace", fontSize:"0.62rem", cursor:"pointer", color:C.muted }}>Cancel</button>
            </div>
          </div>
        </div>
      )}

      {/* HEADER */}
      <div style={{ background:C.navy, padding:"1rem 1.5rem", display:"flex", justifyContent:"space-between", alignItems:"center", borderBottom:`1px solid rgba(184,146,74,0.15)` }}>
        <MGALogo size={0.9} light/>
        <div style={{ display:"flex", gap:"0.75rem", alignItems:"center" }}>
          {origin && mode && !selected && <button onClick={resetMode} style={navBtn}>← Change</button>}
          {origin && !mode && <button onClick={reset} style={navBtn}>← Back</button>}
          {selected && <button onClick={()=>setSelected(null)} style={navBtn}>← Results</button>}
          <a href="https://www.meridiangateadvisory.com/contact/" target="_blank" rel="noreferrer"
            style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.56rem", letterSpacing:"0.1em", textTransform:"uppercase", color:C.gold, border:`1px solid ${C.gold}`, padding:"0.28rem 0.75rem", textDecoration:"none" }}>
            Book Consultation
          </a>
        </div>
      </div>

      {/* CEPA BANNER */}
      <div style={{ background:C.darkAlt, padding:"0.45rem 1.5rem", borderBottom:`1px solid rgba(184,146,74,0.2)` }}>
        <span style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.54rem", color:"rgba(255,255,255,0.7)", letterSpacing:"0.04em" }}>
          <strong style={{ color:C.gold }}>CEPA Status:</strong> Signed Sept 24, 2025 · Target entry into force 2026 (ratification pending) · Canada eliminates 90.5% of tariff lines on Indonesian goods · All CEPA rates are <em>forward-looking</em>
        </span>
      </div>

      {/* STEP 1 — ORIGIN */}
      {!origin && (
        <div style={{ maxWidth:"680px", margin:"0 auto", padding:"4rem 1.5rem 2.5rem" }}>
          <div style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.54rem", letterSpacing:"0.22em", textTransform:"uppercase", color:C.gold, marginBottom:"1.25rem", opacity:0.9 }}>
            Canada – Indonesia Trade Intelligence
          </div>
          <h1 style={{ fontFamily:"'Cormorant Garamond',serif", fontSize:"clamp(2.2rem,5vw,3.4rem)", fontWeight:600, lineHeight:1.15, marginBottom:"1rem", letterSpacing:"-0.01em", color:C.navy }}>
            Know your tariff.<br/><em style={{ color:C.gold, fontStyle:"italic" }}>Before</em> you trade.
          </h1>
          <p style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.9rem", color:C.muted, lineHeight:1.75, maxWidth:"480px", fontWeight:400, marginBottom:"3rem" }}>
            Get HS codes, current MFN rates, upcoming CEPA preferential rates, compliance requirements, and market signals — across <strong style={{ color:C.navy }}>{products.length}</strong> Canada–Indonesia trade categories.
          </p>
          <SL t="Step 1 — Where are you based?"/>
          <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr", gap:"1px", background:C.border, maxWidth:"480px" }}>
            {[["CA","Canada",["I am based in Canada","Export to or import from Indonesia"]],
              ["ID","Indonesia",["I am based in Indonesia","Export to or import from Canada"]]
            ].map(([code, name, lines]) => (
              <button key={code} onClick={() => setOrigin(code)}
                style={{ background:C.white, border:"none", padding:"1.5rem 1.25rem", cursor:"pointer", textAlign:"left", transition:"background 0.15s" }}
                onMouseEnter={e=>e.currentTarget.style.background=C.light}
                onMouseLeave={e=>e.currentTarget.style.background=C.white}>
                <div style={{ marginBottom:"0.6rem" }}><Flag country={code} h={24}/></div>
                <div style={{ fontFamily:"'Cormorant Garamond',serif", fontWeight:600, fontSize:"1.1rem", color:C.navy, marginBottom:"0.25rem" }}>{name}</div>
                {lines.map((l,i) => <div key={i} style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.72rem", color:C.muted, lineHeight:1.5 }}>{l}</div>)}
              </button>
            ))}
          </div>
          <div style={{ marginTop:"2.5rem", padding:"0.9rem 1.1rem", background:C.white, borderLeft:`3px solid ${C.gold}`, fontSize:"0.7rem", color:C.muted, lineHeight:1.6 }}>
            Data sourced from CBSA, Global Affairs Canada CEPA official documents, and Indonesian trade regulations. Tariff data verified as of April 2026. Verify all classifications before shipping.
          </div>
        </div>
      )}

      {/* STEP 2 — MODE */}
      {origin && !mode && (
        <div style={{ maxWidth:"680px", margin:"0 auto", padding:"3.5rem 1.5rem 2.5rem" }}>
          <div style={{ display:"flex", alignItems:"center", gap:"0.75rem", marginBottom:"2.5rem" }}>
            <Flag country={origin} h={22}/>
            <span style={{ fontFamily:"'Cormorant Garamond',serif", fontWeight:600, fontSize:"1.1rem", color:C.navy }}>{homeName}</span>
            <span style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.56rem", color:C.gold, opacity:0.7 }}>selected</span>
          </div>
          <SL t="Step 2 — What do you want to do?"/>
          <div style={{ display:"grid", gridTemplateColumns:"1fr 1fr", gap:"1px", background:C.border, maxWidth:"480px" }}>
            {[
              ["export", isCA
                ? ["Canada → Indonesia","Export to Indonesia","See what Indonesia requires to let your goods in + the tariff Indonesia charges"]
                : ["Indonesia → Canada","Export to Canada","See what Canada requires to let your goods in + the tariff Canada charges"]],
              ["import", isCA
                ? ["Canada ← Indonesia","Import from Indonesia","See what Canada requires to let goods in + the tariff Canada charges"]
                : ["Indonesia ← Canada","Import from Canada","See what Indonesia requires to let goods in + the tariff Indonesia charges"]],
            ].map(([m, [arrow, title, detail]]) => (
              <button key={m} onClick={() => setMode(m)}
                style={{ background:C.white, border:"none", padding:"1.5rem 1.25rem", cursor:"pointer", textAlign:"left" }}
                onMouseEnter={e=>e.currentTarget.style.background=C.light}
                onMouseLeave={e=>e.currentTarget.style.background=C.white}>
                <div style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.75rem", marginBottom:"0.6rem", color:C.gold, letterSpacing:"0.05em" }}>{arrow}</div>
                <div style={{ fontFamily:"'Cormorant Garamond',serif", fontWeight:600, fontSize:"1.05rem", color:C.navy, marginBottom:"0.3rem" }}>{title}</div>
                <div style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.72rem", color:C.muted, lineHeight:1.5 }}>{detail}</div>
              </button>
            ))}
          </div>
        </div>
      )}

      {/* STEP 3 — SEARCH / BROWSE */}
      {origin && mode && !selected && (
        <div style={{ maxWidth:"740px", margin:"0 auto", padding:"1.75rem 1.5rem" }}>
          {/* Context strip */}
          <div style={{ display:"flex", alignItems:"center", gap:"0.65rem", marginBottom:"1.5rem", padding:"0.75rem 1.1rem", background:C.white, borderLeft:`3px solid ${C.gold}` }}>
            <Flag country={origin} h={18}/>
            <span style={{ fontFamily:"'Inter',sans-serif", fontWeight:600, fontSize:"0.82rem", color:C.navy }}>{homeName}</span>
            <span style={{ color:C.border, fontSize:"1rem" }}>·</span>
            <span style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.8rem", color:C.navy }}>{modeLabel}</span>
            <span style={{ marginLeft:"auto", fontFamily:"'DM Mono',monospace", fontSize:"0.57rem", color:C.muted }}>{filtered.length} products</span>
          </div>

          {/* View toggle */}
          <div style={{ display:"flex", gap:"1px", background:C.border, marginBottom:"1.35rem", maxWidth:"240px" }}>
            {[["search","Search"],["browse","Browse"]].map(([v,label]) => (
              <button key={v} onClick={()=>setView(v)}
                style={{ flex:1, padding:"0.5rem", fontFamily:"'DM Mono',monospace", fontSize:"0.58rem", letterSpacing:"0.06em", border:"none", cursor:"pointer",
                  background: view===v ? C.navy : C.white,
                  color: view===v ? C.gold : C.muted }}>
                {label}
              </button>
            ))}
          </div>

          {view === "search" && (
            <>
              <div style={{ display:"flex", border:`1.5px solid ${C.navy}`, background:C.white, marginBottom:"1.25rem" }}>
                <input value={query} onChange={e=>setQuery(e.target.value)}
                  placeholder="Search products, HS codes, or sectors…"
                  style={{ flex:1, padding:"0.8rem 1rem", fontFamily:"'Inter',sans-serif", fontSize:"0.88rem", border:"none", outline:"none", color:C.navy }}/>
                {query && <button onClick={()=>setQuery("")} style={{ background:"transparent", border:"none", padding:"0 0.9rem", color:C.muted, cursor:"pointer", fontSize:"1.1rem" }}>×</button>}
              </div>

              {query.length > 1 && results.length === 0 && (
                <div style={{ padding:"1.25rem", background:C.white, borderLeft:`3px solid ${C.gold}` }}>
                  <div style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.57rem", letterSpacing:"0.1em", textTransform:"uppercase", color:C.gold, marginBottom:"0.4rem" }}>Product not in database</div>
                  <p style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.8rem", color:C.muted, lineHeight:1.6, margin:"0 0 0.75rem" }}>For a custom product analysis — HS classification, tariff brief, and CEPA impact — contact MGA directly.</p>
                  <a href="https://www.meridiangateadvisory.com/contact/"
                    style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.57rem", letterSpacing:"0.1em", textTransform:"uppercase", color:C.white, background:C.navy, padding:"0.42rem 0.9rem", textDecoration:"none", display:"inline-block" }}>
                    Request Custom Brief →
                  </a>
                </div>
              )}

              {results.length > 0 && (
                <div style={{ background:C.white, border:`1px solid ${C.borderLight}` }}>
                  {results.map(p=><ProdRow key={p.id} p={p}/>)}
                </div>
              )}

              {query.length < 2 && popular.length > 0 && (
                <div>
                  <SL t="High-opportunity products"/>
                  <div style={{ display:"flex", flexWrap:"wrap", gap:"0.45rem" }}>
                    {popular.map(p=>(
                      <button key={p.id} onClick={()=>setSelected(p)}
                        style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.75rem", padding:"0.32rem 0.7rem", border:`1px solid ${C.border}`, background:C.white, cursor:"pointer", color:C.navy }}>
                        {p.name}
                      </button>
                    ))}
                  </div>
                </div>
              )}
            </>
          )}

          {view === "browse" && (
            <>
              {sector === null ? (
                <>
                  <SL t="Select a sector"/>
                  <div style={{ background:C.white, border:`1px solid ${C.borderLight}` }}>
                    {visSectors.map(s => {
                      const cnt = sectorProds(s, products, origin, mode).length;
                      return (
                        <button key={s} onClick={()=>setSector(s)}
                          style={{ background:"transparent", border:"none", borderBottom:`1px solid ${C.borderLight}`, padding:"0.82rem 1.1rem", cursor:"pointer", textAlign:"left", display:"flex", justifyContent:"space-between", alignItems:"center", width:"100%" }}
                          onMouseEnter={e=>e.currentTarget.style.background=C.light}
                          onMouseLeave={e=>e.currentTarget.style.background="transparent"}>
                          <span style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.83rem", color:C.navy }}>{s}</span>
                          <span style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.57rem", color:C.gold }}>{cnt}</span>
                        </button>
                      );
                    })}
                  </div>
                </>
              ) : (
                <>
                  <button onClick={()=>setSector(null)}
                    style={{ background:"transparent", border:"none", fontFamily:"'DM Mono',monospace", fontSize:"0.57rem", letterSpacing:"0.08em", color:C.muted, cursor:"pointer", marginBottom:"0.75rem", padding:0 }}>
                    ← All Sectors
                  </button>
                  <SL t={sector}/>
                  <div style={{ background:C.white, border:`1px solid ${C.borderLight}` }}>
                    {sectorProds(sector, products, origin, mode).map(p=><ProdRow key={p.id} p={p}/>)}
                  </div>
                </>
              )}
            </>
          )}
        </div>
      )}

      {/* PRODUCT DETAIL */}
      {origin && mode && selected && pData && (
        <div style={{ maxWidth:"740px", margin:"0 auto", padding:"1.75rem 1.5rem" }}>

          {/* Product header */}
          <div style={{ borderBottom:`1px solid ${C.borderLight}`, paddingBottom:"1rem", marginBottom:"1.25rem" }}>
            <h2 style={{ fontFamily:"'Cormorant Garamond',serif", fontSize:"1.9rem", fontWeight:600, margin:"0 0 0.4rem", letterSpacing:"-0.01em", color:C.navy }}>{selected.name}</h2>
            <div style={{ display:"flex", gap:"0.5rem", alignItems:"center", flexWrap:"wrap" }}>
              {selected.hs !== "N/A" && <span style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.62rem", color:C.muted }}>HS {selected.hs}</span>}
              <span style={{ color:C.border }}>·</span>
              <span style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.62rem", color:C.muted }}>{selected.sector}</span>
              <span style={{ color:C.border }}>·</span>
              <ConfBadge c={pData.conf}/>
              <span style={{ marginLeft:"auto", fontFamily:"'DM Mono',monospace", fontSize:"0.54rem", color:C.muted }}>{modeLabel} · {new Date().toLocaleDateString("en-CA",{year:"numeric",month:"short",day:"numeric"})}</span>
            </div>
          </div>

          {/* Tariff card */}
          {pData.mfn !== "N/A" ? (
            <div style={{ display:"grid", gridTemplateColumns:"1fr 1.5fr", gap:"1px", background:C.border, marginBottom:"1px" }}>
              <div style={{ background:C.white, padding:"1.1rem" }}>
                <SL t="HS Code"/>
                <div style={{ fontFamily:"'DM Mono',monospace", fontSize:"1.5rem", fontWeight:500, color:C.navy, marginBottom:"0.15rem" }}>{selected.hs}</div>
                <div style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.7rem", color:C.muted }}>{selected.sector}</div>
              </div>
              <div style={{ background:C.white, padding:"1.1rem" }}>
                <SL t={pData.tariffTitle}/>
                <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", marginBottom:"0.45rem" }}>
                  <span style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.7rem", color:C.muted }}>
                    Today (MFN)&nbsp;<span style={{ background:C.navy, color:"#fff", fontSize:"0.44rem", padding:"0.07rem 0.28rem", fontFamily:"'DM Mono',monospace", verticalAlign:"middle" }}>NOW</span>
                  </span>
                  <span style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.9rem", fontWeight:500, color:C.navy }}>{pData.mfn}</span>
                </div>
                <div style={{ display:"flex", justifyContent:"space-between", alignItems:"center", marginBottom:"0.5rem" }}>
                  <span style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.7rem", color:C.muted }}>
                    Under CEPA (est. 2026)&nbsp;<span style={{ background:C.green, color:"#fff", fontSize:"0.44rem", padding:"0.07rem 0.28rem", fontFamily:"'DM Mono',monospace", verticalAlign:"middle" }}>COMING</span>
                  </span>
                  <span style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.9rem", fontWeight:500, color:C.green }}>{pData.cepa}</span>
                </div>
                <div style={{ background:"rgba(42,107,74,0.07)", padding:"0.42rem 0.65rem", borderLeft:`2px solid ${C.green}`, fontFamily:"'Inter',sans-serif", fontSize:"0.68rem", color:C.green, lineHeight:1.45 }}>{pData.saving}</div>
              </div>
            </div>
          ) : (
            <div style={{ background:C.white, padding:"1.1rem", marginBottom:"1px", borderLeft:`3px solid ${C.gold}` }}>
              <SL t="Agreement Coverage"/>
              <p style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.8rem", color:C.muted, lineHeight:1.6, margin:0 }}>{pData.cepa}</p>
            </div>
          )}

          {/* Requirements */}
          {pData.reqs && pData.reqs.length > 0 && (
            <div style={{ background:C.white, padding:"1.1rem", marginBottom:"1px" }}>
              <SL t={pData.regsTitle}/>
              <ul style={{ listStyle:"none", display:"flex", flexDirection:"column", gap:"0.5rem" }}>
                {pData.reqs.map((r,i) => (
                  <li key={i} style={{ display:"flex", gap:"0.6rem", fontFamily:"'Inter',sans-serif", fontSize:"0.8rem", lineHeight:1.55, color:"#2C3E50" }}>
                    <span style={{ width:"4px", height:"4px", borderRadius:"50%", background:C.gold, flexShrink:0, marginTop:"0.55rem", display:"inline-block" }}/>
                    {r}
                  </li>
                ))}
              </ul>
            </div>
          )}

          {/* Market signal */}
          {pData.market && pData.market !== "N/A" && (
            <div style={{ background:C.white, padding:"1.1rem", marginBottom:"1px" }}>
              <SL t={pData.marketTitle}/>
              <p style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.8rem", color:"#3A4A5A", lineHeight:1.7, marginBottom:"0.8rem" }}>{pData.market}</p>
              <div style={{ height:"3px", background:C.borderLight, marginBottom:"0.35rem" }}>
                <div style={{ height:"100%", width:`${pData.score}%`, background:C.gold, transition:"width 0.6s ease" }}/>
              </div>
              <div style={{ display:"flex", justifyContent:"space-between", fontFamily:"'DM Mono',monospace", fontSize:"0.55rem", color:C.muted }}>
                <span>Low opportunity</span>
                <span style={{ color:C.navy, fontWeight:500 }}>{pData.score} / 100</span>
                <span>High opportunity</span>
              </div>
            </div>
          )}

          {/* CEPA prep box */}
          <div style={{ background:C.navy, padding:"1rem 1.1rem", marginBottom:"1px", borderLeft:`3px solid ${C.gold}` }}>
            <SL t="CEPA Preparation — Act Now"/>
            <p style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.77rem", color:"rgba(255,255,255,0.75)", lineHeight:1.65, margin:0 }}>
              The Canada–Indonesia CEPA was signed September 24, 2025. Target entry into force is 2026, pending parliamentary ratification. Use this window to establish relationships, verify rules of origin eligibility, and prepare compliance documentation — so you capture the tariff advantage from day one.
            </p>
          </div>

          {/* CTA */}
          <div style={{ background:C.darkAlt, padding:"1.5rem 1.25rem", display:"flex", flexWrap:"wrap", gap:"1.25rem", alignItems:"center", justifyContent:"space-between", marginBottom:"0.75rem", borderTop:`1px solid rgba(184,146,74,0.2)` }}>
            <div style={{ flex:1, minWidth:"200px" }}>
              <div style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.48rem", letterSpacing:"0.14em", textTransform:"uppercase", color:C.gold, opacity:0.7, marginBottom:"0.35rem" }}>Next step with MGA</div>
              <div style={{ fontFamily:"'Cormorant Garamond',serif", fontSize:"1.2rem", color:C.white, marginBottom:"0.35rem", lineHeight:1.3, fontWeight:600 }}>Ready to move on {selected.name}?</div>
              <div style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.71rem", color:"rgba(255,255,255,0.5)", lineHeight:1.55 }}>MGA provides market entry strategy, buyer/supplier introductions, and CEPA compliance advisory for Canada–Indonesia trade.</div>
            </div>
            <a href="https://www.meridiangateadvisory.com/contact/" target="_blank" rel="noreferrer"
              style={{ background:C.gold, color:C.white, padding:"0.8rem 1.4rem", fontFamily:"'DM Mono',monospace", fontSize:"0.6rem", letterSpacing:"0.12em", textTransform:"uppercase", textDecoration:"none", whiteSpace:"nowrap", fontWeight:500 }}>
              Book with MGA →
            </a>
          </div>

          {/* Disclaimer */}
          <div style={{ padding:"0.75rem 1rem", background:C.white, borderLeft:`2px solid ${C.border}`, fontFamily:"'Inter',sans-serif", fontSize:"0.66rem", color:C.muted, lineHeight:1.55 }}>
            <ConfBadge c={pData.conf}/>{" "}
            {pData.conf==="I" ? "Tariff staging based on official category-level CEPA summaries — verify against Annex 2-A tariff schedules." : "Cross-referenced against CBSA and Global Affairs Canada official CEPA documents."}{" "}
            Verify all HS classifications with CBSA before importing or exporting. CEPA rates apply only upon entry into force with rules of origin compliance. Not legal or trade compliance advice.
          </div>
        </div>
      )}

      {/* FOOTER */}
      <div style={{ background:C.navy, borderTop:`1px solid rgba(184,146,74,0.2)`, padding:"1.5rem 1.5rem", display:"flex", justifyContent:"space-between", alignItems:"center", flexWrap:"wrap", gap:"1rem", marginTop:"3rem" }}>
        <MGALogo size={0.8} light/>
        <div style={{ display:"flex", gap:"1.5rem", alignItems:"center" }}>
          {[["About","https://www.meridiangateadvisory.com/about/"],
            ["Services","https://www.meridiangateadvisory.com/about/"],
            ["Contact","https://www.meridiangateadvisory.com/contact/"]
          ].map(([l,href])=>(
            <a key={l} href={href} target="_blank" rel="noreferrer"
              style={{ fontFamily:"'Inter',sans-serif", fontSize:"0.72rem", color:"rgba(255,255,255,0.5)", textDecoration:"none", letterSpacing:"0.05em", textTransform:"uppercase" }}>{l}</a>
          ))}
          <button onClick={()=>setAdminInput(true)}
            style={{ background:"transparent", border:"none", color:C.navy, fontSize:"0.5rem", cursor:"pointer", padding:"0.2rem 0.4rem", userSelect:"none", lineHeight:1 }}>·</button>
        </div>
        <div style={{ fontFamily:"'DM Mono',monospace", fontSize:"0.52rem", letterSpacing:"0.1em", textTransform:"uppercase", color:"rgba(255,255,255,0.3)" }}>© 2025 Meridian Gate Advisory Inc.</div>
      </div>
    </div>
  );
}
