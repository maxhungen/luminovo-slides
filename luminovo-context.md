# Luminovo Slide Context

A reference the slide skill reads before building a deck. It captures what Luminovo is, the proof, and the rules for **what to put on a slide for a given customer situation**. Source: luminovo.com (home, case studies, integrations, security), scanned June 2026.

Writing rules for every slide generated from this file:
- Simple, professional language. Short sentences.
- Do not use double dashes. Use a period, comma, colon, or parentheses instead.
- No buzzwords. Avoid "seamless", "game changer", "synergy", "leverage", "cutting edge", "revolutionize", "best in class". Plain words win.
- Prove claims with concrete numbers and named customers, not adjectives.
- Treat the public figures below as company marketing numbers. For a specific deal, use that customer's own numbers and confirm any claim before sharing (see the checklist in SKILL.md).

---

## 1. What Luminovo is (one line)

One platform for electronics teams to monitor, source, and quote PCBAs in one place, built specifically for electronics and running on one connected set of data.

Two core products:
- **Quoting Intelligence** for EMS providers. Quote faster and win more deals.
- **Procurement Intelligence** for OEMs. Lower material cost and get supplier transparency.

---

## 2. Who you are talking to

Decide the audience first. It sets the lead product, the pains, and the proof.

| Audience | Lead product | What they care about | What hurts today |
|---|---|---|---|
| **EMS provider** | Quoting Intelligence | Quote speed, RFQ throughput, winning deals, less overtime | Slow manual quoting, version chaos in email, losing deals on response time |
| **OEM** | Procurement Intelligence | Material cost savings, supplier transparency, demand bundling | High component cost, no market price leverage, fragmented data |

Both audiences also care about: supply chain risk, data quality, fitting their existing systems, and security. Cover these only when they come up.

---

## 3. The core promise and the proof

Public proof points to use on a cover, an executive summary, or a proof slide:
- 90% faster RFQ turnaround
- 5% material cost reduction
- 10% more revenue
- 300+ customers
- 4.8 rating on Capterra

Rule: lead with the one number that matches the audience. EMS leads with the 90% faster RFQ figure. OEM leads with the 5% material cost figure. When you have the customer's own number, use that instead and keep the company number as backup.

---

## 4. Products and add-ons

Full detail and ready slides live in `luminovo-product-slides.html`. Short version for routing:

- **Quoting Intelligence** (EMS core). Add-ons: Customer Portal, Manufacturing, Risk (SCRM), PCB Pricing, Strategic Sourcing, Supplier (SRM).
- **Procurement Intelligence** (OEM core). Includes Strategic Sourcing. Add-ons: Risk (SCRM), Manufacturing, PCB Pricing, Supplier (SRM).
- **Platform foundation** sits under everything: BOM management and scrubbing, AI data processing, 100+ integrations, real time collaboration, ElectronicsGPT.
- Strategic Sourcing and Supplier (SRM) are not shipped yet. Always mark them "coming soon".

---

## 5. Proof bank (named customer stories)

Pick the story closest to the prospect's segment and need. Lead with the result, then one line of context. Most stories are EMS quoting wins, so a few are flagged for OEM and for supplier or risk topics.

| Customer | Best for | Result to cite |
|---|---|---|
| Datalink Electronics | EMS, growth | Unlocked GBP 3 million in new turnover. Moved from reactive to proactive. |
| Sigmatron | EMS, global, scale | Global quoting went from weeks to hours. |
| Omega EMS | EMS, team capacity | Same day quotes with zero overtime. |
| Kessler | EMS, standardization | Quoting and procurement went from days to hours. |
| Ihlemann | EMS, speed | RFQ times dropped from weeks to days. |
| Jopp Electronics | EMS, complex projects | Quotes complex projects in record time. |
| Nordes EMS | EMS, RFQ process | Faster and smarter RFQ process. |
| INTUS Elektronik | EMS, data quality | Faster quoting and better data quality. |
| Price Electronics | EMS, collaboration | End to end quoting in one system, faster quotes. |
| TSTRONIC | EMS, efficiency | Improved quoting efficiency. |
| Lacon | EMS, growth | Turned manual overload into a growth path. |
| Hekatron | Prototyping speed | Functional prototypes in 15 days. |
| Zollner | Prototyping | Optimized its Rapid Sample prototyping unit. |
| BMK | Prototyping | Optimized rapid prototyping from series production. |
| Leuze | OEM, cost and risk | Optimized production cost and reduced risk. Moved from estimates to evidence. |
| TQ | OEM, supplier management | Full supply chain transparency in supplier management. |
| Grossenbacher Systeme AG | Supplier management | Reshaped supplier management. |
| Nova Engineering | EMS, switch | Switched to Luminovo for two clear reasons. |

Generic results you can cite when a named story is not needed: 50% faster processes, live in four weeks from first meeting to cost savings.

Rule: match segment first (EMS vs OEM), then topic (speed, cost, supplier, prototyping, risk). Use one story per proof slide. Do not stack logos without a result.

---

## 6. Integrations (for "does it work with our systems?")

Luminovo connects to 123+ systems and offers a custom API. Connect ERP or PLM data, then enrich it with part data providers and your distributors or PCB suppliers.

| Category | Named examples to show |
|---|---|
| ERP | SAP, Microsoft Dynamics NAV and 365, Infor, Epicor, Oracle E-Business Suite, IFS, proALPHA, Sage, Odoo, Monitor, ABAS, Acumatica |
| PLM | Aras, Windchill |
| Component distributors | Digikey, Mouser, Arrow, Avnet, Farnell, Newark, TTI, Rutronik, Würth Elektronik, RS, Future Electronics, Heilind, LCSC |
| PCB suppliers | Beta Layout, Gatema, iCape Group, EPN Electroprint, MOS Electronic |
| Part data providers | Octopart, Nexar, Silicon Expert, TME, Trusted Parts |
| Sustainability | Sluicebox (product carbon footprint) |
| Custom | Luminovo API |

Rule: if the prospect names a system that is on the list, show it on an integration slide and say it is supported. If it is not on the list, point to the API and the 123+ count. Do not claim an integration you cannot confirm.

---

## 7. Security and compliance (for regulated or IT led buyers)

| Topic | What to state |
|---|---|
| Certifications | ISO 27001:2022 (certified since June 2023). SOC 2 Type II. |
| Defense | ITAR registered (Luminovo Inc. with the U.S. DDTC). |
| Hosting and residency | Choice of Frankfurt (Germany) or Virginia (USA), on Microsoft Azure. GovCloud available for regulated workloads. |
| Data privacy | GDPR compliant by default. EU data residency available. Customer data deleted 30 days after the agreement ends or on written request. |
| Encryption | AES 256 bit at rest (FIPS 140-2 validated modules). TLS 1.2 and above in transit. |
| Access | Single Sign On and SAML on Enterprise. Role based access control. Optional multi factor authentication. |
| Availability | Automatic backups with zone redundant storage, 14 day retention. DDoS protection via Cloudflare. |
| Separation | Multi tenant architecture with separation at the database level. |

Rule: include a security slide when the buyer is in automotive, medical, or defense, when IT or security is in the room, or when a security questionnaire is mentioned. Lead with ISO 27001, EU hosting, and GDPR. Add ITAR only for defense.

---

## 8. Objections to expect, and what to show

The core routing table. When the customer raises one of these, respond in one or two plain sentences and show the matching slide.

| They say | Short response | Show this slide |
|---|---|---|
| It is too expensive, or the ROI is unclear | Build the case on their numbers. One avoided redesign or a few points of material cost usually covers the year. | Business case and ROI (bars or before and after) |
| We already use Silicon Expert or another data tool | Keep it. Luminovo connects to it and makes the data act on your BOM. | Comparison: data service vs action, plus Risk |
| Does it work with our ERP and systems? | 123+ integrations, plus an API for anything else. | Integrations |
| Is our data safe, we are regulated | ISO 27001, EU hosting, GDPR by default. ITAR for defense. | Security and compliance |
| Will this disrupt our process, setup looks long | It extends what you run today. Customers go live in about four weeks. | Implementation roadmap |
| Does it fit our industry and size? | Show a customer like them. | Relevant case study from the proof bank |
| We do this manually, or we built our own | Manual work caps speed and ties up the team. Show the time saved. | Before and after, plus a speed case study (Omega, Kessler) |
| We are an OEM, this looks built for EMS | Procurement Intelligence is the OEM product. Cost and supplier focus. | Procurement Intelligence, plus Leuze or TQ |
| Will the team actually use it? | Real time collaboration and a customer portal lower the effort. | Platform and Customer Portal |

---

## 9. What they care about, and what to lead with

Route by the interest the customer shows.

| Interest | Lead product | Proof to pair |
|---|---|---|
| Quote speed and RFQ throughput | Quoting Intelligence | Sigmatron, Omega, Kessler, Ihlemann |
| Material cost savings | Procurement Intelligence | Leuze, the 5% figure |
| Supplier transparency and management | Supplier (SRM, coming soon) | TQ, Grossenbacher |
| Supply chain risk and shortages | Risk (SCRM) | Leuze |
| Prototyping speed | Quoting Intelligence and Manufacturing | Hekatron, Zollner, BMK |
| PCB cost and pricing | PCB Pricing | none needed, show the instant price |
| Growth and new revenue | Quoting Intelligence | Datalink (GBP 3 million) |

---

## 10. Default deck shape

When there is no special signal, build in this order and let the context above swap slides in and out:
1. Cover (customer name and modules in the offer)
2. Agenda
3. Current challenges at the customer
4. The platform and the modules in scope
5. Comparison vs the status quo or a data only tool
6. One proof story that matches the customer
7. Business case and ROI on their numbers
8. Security or integrations only if it came up
9. Closing with the next step and the account contact
