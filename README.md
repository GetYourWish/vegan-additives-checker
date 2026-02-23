# 🐰 Vegan Additives Checker

A free, open-source tool to check if product ingredients are vegan-friendly. Instantly identify animal-derived additives, E-numbers, and hidden non-vegan ingredients.

## ✨ Features

**Core Functionality**
- **Instant checking** - Paste ingredients and get results immediately
- **Smart ingredient masking** - Won't false-flag "coconut milk" as containing dairy
- **E-number normalization** - Handles `E120`, `E 120`, `E-120` variants correctly
- **Phrase-based matching** - Matches full ingredient names, not just individual words

**User Experience**
- **Multilingual** - English, French, and Arabic support with RTL layout
- **5 theme options** - Dark, Light, Vegan Green, Navy, Rose
- **Copy & Share** - Export results to clipboard or share natively on mobile
- **Toast notifications** - Clear feedback for user actions

**Accessibility**
- **Screen reader support** - Full ARIA attributes throughout
- **Keyboard navigation** - All interactive elements are keyboard-accessible
- **Live announcements** - Status changes announced to assistive technologies

**Privacy & Performance**
- **100% offline** - No internet required after first load
- **No ads, no tracking** - Privacy-first, no data collected
- **Single file** - Everything contained in one HTML file

## 🚀 Quick Start

1. Download `index.html`
2. Open it in any web browser
3. Paste an ingredients list
4. Review flagged items

## 📊 How It Works

The tool categorizes ingredients into five status levels:

### 🔴 Red — Definitely Animal
No ambiguity. These are derived from animals.
- E120 (Carmine/Cochineal) — crushed beetles
- E428/E441 (Gelatine) — boiled bones, skin, tissue
- E542 (Bone Phosphate) — ground cattle/pig bones
- E904 (Shellac) — lac bug secretions
- Vitamin D3 (unspecified) — usually from sheep's wool

### 🟠 Orange — Hidden Animal Ingredients
Names that sound innocent but are animal-derived.
- Casein/Caseinate — milk protein in "non-dairy" products
- Isinglass — fish bladder collagen (beer/wine clarification)
- Castoreum — beaver gland secretion (natural flavouring)
- Chitosan — crustacean shells (fruit pesticide, supplements)
- Whey/Lactose — dairy by-products

### 🔵 Blue — Grey Area (Verify Source)
Can be either plant-based or animal-derived. Check with manufacturer.
- E322 (Lecithins) — usually soy, but can be egg
- E471 (Mono/diglycerides) — common in bread, source varies
- E470 (Stearates) — often plant-based, sometimes animal
- Natural Flavours — blanket term, can hide animal ingredients
- E270 (Lactic Acid) — usually vegan fermentation, rarely dairy

*Note: Many grey-area additives are increasingly vegan by default in Western markets, but this varies by manufacturer.*

### 🟡 Yellow — Trace Warning
Product contains a "may contain traces" or cross-contamination warning.
- Safe for vegans (no animal exploitation involved)
- Unsafe for those with allergies
- Appears when phrases like "produced in a facility that handles milk" are detected

### 🟢 Green — No Animal Ingredients Detected
No flagged ingredients found in the database.
- **Always verify the original product label** as a final step
- The tool may not recognize uncommon names, typos, or new additives

## 🗄️ Database Coverage

The tool includes **130+ additives and ingredient aliases**, including:
- E-number codes with variant formatting support
- Common ingredient names in multiple languages
- Hidden/sneaky names for animal products
- Grey-area additives requiring verification

## 🌍 Languages Supported

| Language | Status |
|----------|--------|
| English | ✅ Complete |
| Français (French) | ✅ Complete |
| العربية (Arabic) | ✅ Complete with RTL support |

## ⚠️ Important Disclaimer

**This is a reference helper tool, NOT a certification.** Always verify the original product label before purchase.

The tool may:
- Miss typos, misspellings, or uncommon ingredient names
- Not recognize regional naming variations
- Not include recently approved additives
- Have OCR errors from pasted text affect results
- Not detect processing agents (e.g., isinglass in wine) that aren't listed

**When in doubt, contact the manufacturer directly.**

## 🔧 Technical Notes

For developers and contributors:

### Ingredient Matching Logic
- **Vegan compound masking** — Prevents false positives (e.g., "coconut milk" won't trigger "milk")
- **Phrase-based matching** — Splits search terms by pipe `|` and matches full phrases, not individual words
- **E-number normalization** — Regex normalizes `E 120`, `E-120`, `E.120` to `E120` before matching
- **Word boundaries** — Uses `\b` regex boundaries to prevent partial matches

### Adding New Ingredients
Each additive entry follows this structure:
```html
<div class="additive" 
     data-category="red|orange|grey" 
     data-search="E123|alternate name|autre nom|اسم آخر">
  <span class="code">E123</span>
  <span class="name en-only">English Name</span>
  <span class="name fr-only">Nom Français</span>
  <span class="name ar-only">الاسم العربي</span>
  <span class="description en-only">English description.</span>
  <span class="description fr-only">Description française.</span>
  <span class="description ar-only">وصف عربي.</span>
</div>
```

The `data-search` attribute accepts pipe-separated phrases in any language.

## 🤝 Contributing

Contributions are welcome! Here's how to help:

### Adding Missing Additives
1. Find a reliable source (E-number database, manufacturer info)
2. Add entry to the correct category in `index.html`
3. Include translations for all three languages
4. Submit a pull request with sources

### Reporting Issues
- Found incorrect data? [Open an Issue](../../issues)
- Wrong translation? Let us know!
- False positive/negative? Include the ingredients list you tested

### Adding Languages
Want to translate into another language?
1. Fork the repo
2. Add translations following the existing `en-only`/`fr-only`/`ar-only` pattern
3. Add the language to `translations` object in JavaScript
4. Add to `hiddenRedList`, `veganCompounds`, and `tracePatterns` objects
5. Submit a pull request

## 📝 License

MIT License — Use, modify, and share freely. See [LICENSE](LICENSE) for details.

---

## 📜 Changelog

### v1.1.0 — Current
- Added 15+ new additives (E428, E542, E640, E442, E430-436, E252, E415, E270, E325-327, E470, Chitosan)
- Implemented Copy & Share functionality
- Full ARIA accessibility support
- Fixed placeholder localization on initial load
- Improved E-number normalization
- Enhanced vegan compound masking
- Updated descriptions with modern manufacturing context

### v1.0.0 — Initial Release
- Core ingredient checking functionality
- Three-language support (EN, FR, AR)
- Five theme options
- Three confidence categories + trace warnings

---

## 💡 Roadmap

Ideas for future development:

| Idea | Status |
|------|--------|
| Expand additive database | ✅ Ongoing |
| Accessibility improvements | ✅ Complete |
| Copy/Share functionality | ✅ Complete |
| Additional languages | 🔜 Help wanted |
| Brand-specific databases | 📋 Planned |
| Barcode lookup integration | 📋 Under consideration |

Have an idea? [Open a discussion](../../discussions) or submit a pull request!

---

Made with 💚 for the vegan community
