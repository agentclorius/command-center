# Scandic IT Website Structure

**Date:** 17. februar 2026  
**Tech Stack:** Astro + Tailwind CSS  
**Domain:** scandic-it.com

---

## Site Architecture

```
scandic-it.com/
├── / (Home)
├── /services
│   ├── /itad (IT Asset Disposition)
│   ├── /data-destruction (Data Erasure & Destruction)
│   ├── /box-programme (Box Programme / Home Collection)
│   ├── /refurbishment (Device Refurbishment)
│   └── /recycling (E-Waste Recycling)
├── /about
├── /sustainability
├── /certifications
├── /contact
└── /blog (future)
```

---

## Page Specifications

### 1. Home Page (/)

**Hero Section:**
- Headline: "Sikker ITAD med fuld sporbarhed"
- Subheadline: "Vi håndterer udtjente IT-aktiver fra afhentning til certificeret bortskaffelse"
- CTA: "Få et tilbud" / "Book afhentning"
- Trust badges: R2, NAID, ISO certifications

**Key Sections:**
1. **Services Overview** — 4-5 service cards with icons
2. **Why Scandic IT** — USPs (15+ års erfaring, certificeret, dansk)
3. **Process** — Simple 4-step visual (Kontakt → Afhentning → Behandling → Rapport)
4. **Certifications** — Logo row
5. **Testimonials** — Client quotes (if available)
6. **CTA** — Contact form or booking

---

### 2. Services Pages (/services/*)

#### /services/itad
**IT Asset Disposition**
- What we do: Full lifecycle management of retired IT assets
- Process: Audit → Erasure → Grading → Resale/Recycling
- Benefits: Value recovery, compliance, sustainability
- CTA: Request quote

#### /services/data-destruction
**Data Erasure & Destruction**
- Software-based erasure (NIST 800-88 compliant)
- Physical destruction (shredding)
- Certificate of destruction
- On-site options available

#### /services/box-programme
**Box Programme**
- Employee home collection via courier
- Parcel shop drop-off
- Ideal for hybrid/remote workforce
- Branded packaging options

#### /services/refurbishment
**Device Refurbishment**
- Diagnostics and testing
- Repairs (keyboard, battery, screen)
- Re-imaging and configuration
- Grading (A/B/C)

#### /services/recycling
**E-Waste Recycling**
- Certified recycling of non-reusable equipment
- Zero landfill policy
- Environmental certificates
- Recycling reports

---

### 3. About Page (/about)

**Sections:**
1. **Vores Historie** — Founded 2016 by Kasper & Mike, 15+ years ITAD experience
2. **Teamet** — Key people (optional photos)
3. **Vores Værdier** — Trust, sustainability, security
4. **Kunder** — Industries served (without naming specific clients unless approved)

---

### 4. Sustainability Page (/sustainability)

**Focus:**
- Circular economy approach
- E-waste statistics (250M corporate devices/year)
- Environmental impact of refurbishment vs. recycling
- CO2 savings calculator (future feature)
- UN SDG alignment

---

### 5. Certifications Page (/certifications)

**List:**
- R2 (Responsible Recycling)
- NAID (Data Destruction)
- ISO 14001 (Environmental)
- ISO 27001 (Information Security)
- ISO 9001 (Quality Management)

**Per certification:**
- Logo
- What it means
- How it benefits clients

---

### 6. Contact Page (/contact)

**Elements:**
- Contact form (Name, Company, Email, Phone, Message)
- Direct contact info (phone, email)
- Address with map
- Business hours
- Quick quote request option

---

## Design Guidelines

### Colors (matching Returna for consistency, can adjust)
- Primary Green: #00A651
- Dark Green: #008C44
- Accent: #26A69A
- Background: #f8faf9
- Text: #1e293b

### Typography
- Font: Inter
- Headings: 700 weight
- Body: 400 weight

### Imagery
- Professional photos of ITAD operations (warehouse, processing)
- Device images (laptops, servers)
- Team photos (if available)
- Certification badges

---

## Content Priorities (Phase 1)

### Must Have:
1. Home page with clear value proposition
2. Services overview
3. Contact page with form
4. Basic about page

### Nice to Have:
1. Individual service pages
2. Sustainability page
3. Blog infrastructure
4. Danish/English toggle

---

## SEO Keywords

**Primary:**
- ITAD Danmark
- IT asset disposition
- Datasletning certificeret
- E-affald håndtering
- Computer genbrug virksomhed

**Secondary:**
- Box programme Danmark
- Sikker harddisk destruktion
- ISO 27001 ITAD
- R2 certificeret recycling
- NAID certificeret

---

## Technical Requirements

### Astro + Tailwind Setup
```bash
npm create astro@latest scandic-it-web
cd scandic-it-web
npx astro add tailwind
```

### Key Features:
- Static site generation (fast, SEO-friendly)
- Contact form → email integration (Formspree or similar)
- Mobile responsive
- Cookie consent (GDPR)
- Analytics (Plausible or GA4)

---

## Next Steps

1. [ ] Approve site structure
2. [ ] Write homepage copy (DA + EN)
3. [ ] Gather imagery (warehouse, team, devices)
4. [ ] Set up Astro project
5. [ ] Build homepage
6. [ ] Build contact page
7. [ ] Deploy to staging

---

*Draft by Clorius. Ready for Kasper's review.*
