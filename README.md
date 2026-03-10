# 사상의학 API — Sasang Constitutional Medicine API

**The world's first open REST API for Korean Sasang constitutional medicine.**

Free · Static · No auth · No rate limits · CC BY 4.0

---

## What is Sasang Medicine?

Sasang constitutional medicine (사상의학) was systematized by Korean physician **Lee Je-ma (이제마)** in his 1894 text *Donguisusebowon* (동의수세보원). It classifies all people into four constitutional types — each with distinct physiology, metabolism, personality, and responses to food and herbs.

| Type | Korean | Hanja | Population | Strong Organ | Weak Organ | Thermal Nature |
| --- | --- | --- | --- | --- | --- | --- |
| Tae-Yang | 태양인 | 太陽人 | < 1% | Lung (dispersal) | Liver (storage) | Hot |
| So-Yang | 소양인 | 少陽人 | ~30% | Spleen (digestion) | Kidney (cooling) | Hot |
| Tae-Eum | 태음인 | 太陰人 | ~50% | Liver (storage) | Lung (dispersal) | Neutral-warm |
| So-Eum | 소음인 | 少陰人 | ~20% | Kidney (cooling) | Spleen (digestion) | Cold |

**Note:** In SCM, "organs" refer to functional systems, not strict anatomical organs. Lung = respiratory/dispersal. Liver = storage/absorption. Spleen = digestion/intake. Kidney = excretion/cooling.

---

## Quick Start

No API key. No registration. Just fetch.

```javascript
// Get So-Yang constitutional profile
const res = await fetch('https://peaceakame.github.io/sasang-api/api/type/so-yang.json');
const type = await res.json();

console.log(type.tagline);        // "Runs hot · Moves fast · Feels everything loudly"
console.log(type.diet.ginseng);   // "avoid"
```

```python
import requests

r = requests.get('https://peaceakame.github.io/sasang-api/api/herb/ginseng.json')
ginseng = r.json()

for type_id, info in ginseng['constitutional_guidance'].items():
    print(f"{type_id}: {info['recommendation']}")

# tae-yang: strictly_avoid
# so-yang: avoid
# tae-eum: moderate_benefit
# so-eum: highly_beneficial
```

---

## Endpoints

| Endpoint | Description |
| --- | --- |
| `/api/type/index.json` | All four types — summary with organ balance and thermal nature |
| `/api/type/tae-yang.json` | Tae-Yang full profile (diet, herbs, skincare, personality, health) |
| `/api/type/so-yang.json` | So-Yang full profile |
| `/api/type/tae-eum.json` | Tae-Eum full profile |
| `/api/type/so-eum.json` | So-Eum full profile |
| `/api/foods/index.json` | Food recommendations by constitutional type |
| `/api/skincare/index.json` | Skincare ingredients with constitutional compatibility ratings |
| `/api/herb/index.json` | Herb compatibility guide — quick ratings for key herbs |
| `/api/herb/ginseng.json` | Ginseng: detailed safety profile by constitution with alternatives |
| `/api/symptoms/index.json` | Symptom → constitutional type mapping with mechanisms |

---

## Why This Exists

Korea built a **$754M ginseng export industry** while its own medical tradition says approximately 30% of people should actively avoid it and another 50% should use it cautiously. The Sasang framework explains why the same herb, diet, or skincare ingredient works brilliantly for one person and causes adverse reactions in another.

This API makes that clinical knowledge machine-readable for the first time.

### Ginseng Constitutional Safety

| Type | Recommendation | Why |
| --- | --- | --- |
| So-Eum 소음인 | ✅ Highly Beneficial | Provides the warmth and digestive support this cold type lacks |
| Tae-Eum 태음인 | ⚠️ Moderate Benefit | Tolerable, but may promote stagnation without dispersing herbs |
| So-Yang 소양인 | ❌ Avoid | Adds heat to an already hot constitution |
| Tae-Yang 태양인 | 🚫 Strictly Avoid | Maximum Yang + warming tonic = dangerous heat accumulation |

---

## Data Structure

Each type profile includes:
- **Organ balance** — strong/weak organ pair with functional descriptions
- **Thermal nature** — constitutional heat/cold tendency
- **Body characteristics** — build, metabolism, vulnerabilities
- **Personality** — Seong (innate nature), Jeong (emotional disposition), strengths, weaknesses
- **Health tendencies** — common conditions, warning signs, protective factors
- **Diet** — beneficial/harmful foods with ginseng compatibility
- **Skincare** — ingredient compatibility for hanbang skincare
- **Herbs** — beneficial herbs with Latin names and actions, herbs to avoid with reasons
- **Research notes** — genetic, metabolic, and heritability data from modern studies

---

## Use Cases

- **Wellness apps** — personalized supplement and diet recommendations
- **K-beauty tools** — ingredient compatibility engines for constitutional skincare
- **Nutrition trackers** — constitutional food guidance layer
- **Academic research** — structured traditional medicine data
- **Herb safety** — flag herb–constitution conflicts before purchase
- **Cultural heritage** — Korean medicine knowledge preservation

---

## Setup (GitHub Pages)

1. Fork or clone this repo
2. Go to repo **Settings → Pages**
3. Set source to `main` branch, root directory
4. Your API is live at `https://YOUR-USERNAME.github.io/sasang-api/`

All endpoints are static JSON files served directly by GitHub Pages.

---

## Attribution & License

Data derived from the Sasang constitutional medicine tradition codified by **Lee Je-ma (이제마)** in *Donguisusebowon*, 1894.

Compiled and structured by **[hanbangtype.com](https://hanbangtype.com)** — the most user-friendly English-language resource for Sasang constitutional medicine.

**License: CC BY 4.0** — Free to use, modify, and distribute with attribution.

```json
"attribution": "Sasang Constitutional Medicine API — hanbangtype.com"
```

**Disclaimer:** Educational information only. Not medical advice. For constitutional diagnosis, consult a licensed Korean medicine practitioner (한의사).

---

*사상의학 · 동의수세보원 · 이제마 · 1894*
