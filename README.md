# Ex Amore Dei — content library

Catholic texts or texts of Catholic origin for the **Ex Amore Dei** app, published as a content
repository of the [GitDocRead content specification 1.0](https://github.com/pizzonia/gitdocread)
(`gitdocread.yaml`, `works/<work>/<language>/<edition>/`).

**Content policy**: only Catholic texts or texts of Catholic origin; every text of Divinum
Officium is accepted (GitDocRead requirement SYS025).

## Contents

| Work | Kind | Editions | Source | License |
|------|------|----------|--------|---------|
| `bible` | scripture | **la** Biblia Sacra Vulgata Clementina (73 books), **en** Douay-Rheims, Challoner revision (73 books) | [open-bibles](https://github.com/seven1m/open-bibles) | public domain |
| `bible` (psalter) | scripture | psalter of the Roman Breviary (150 psalms): **la**, **it**, **en**, **he** | [Divinum Officium](https://github.com/DivinumOfficium/divinum-officium) | MIT |
| `our-father`, `hail-mary`, `gloria-patri`, `apostles-creed`, `confiteor`, `te-deum`, `requiem-aeternam`, `fidelium-animae`, `deus-in-adjutorium` | prayer, creed, hymn, liturgy | la, it, en | Divinum Officium | MIT |
| `alma-redemptoris-mater`, `ave-regina-caelorum`, `regina-caeli`, `salve-regina` | hymn (Marian antiphons) | la, it, en | Divinum Officium | MIT |
| `ordo-missae` | liturgy | la, it, en | Divinum Officium | MIT |
| `baltimore-catechism` | catechism | en (No. 1, 1885) | [Project Gutenberg #14551](https://github.com/GITenberg/A-Catechism-of-Christian-Doctrine_14551) | public domain |

All Bible editions use the numbering of the Clementine Vulgate (`vul-clementine`).

## Licenses

- Texts of Divinum Officium: MIT License, © Divinum Officium project —
  [LICENSES/MIT-DivinumOfficium.txt](LICENSES/MIT-DivinumOfficium.txt).
- Clementine Vulgate, Douay-Rheims, Baltimore Catechism: public domain.
- The license of every edition is also given in its `edition.yaml` (`copyright`, `license`, `source`).
- Manifests and this README: CC0-1.0.

## How it is built

All files under `works/` and `gitdocread.yaml` are generated; do not edit them by hand.

```bash
python3 -I tools/import/build_library.py SOURCES_DIR /path/to/examoredei-library
python3 tools/validate_content.py /path/to/examoredei-library --update-hashes
```

(commands of the [gitdocread](https://github.com/pizzonia/gitdocread) repository). Sources used
for this version:

| Source | Commit |
|--------|--------|
| Divinum Officium | `d6c806624c9dcff6c715ef2d4abc3c9dee25d412` |
| open-bibles | `8b330654ade69f7c96268c761da18dc83a1f49b7` |
| gitdocread (converter, branch `dev`) | `dd09eeb8ab067276a0ea89538dd4b10f2a9db155` |

## Known limits

- **Parts that vary by day** (introit, collect, readings, …) are not in the Ordinary of the Mass.
- **Parallel view**: every work with several languages can be read in parallel. Translations are
  numbered as the Latin text (automatic alignment, division by division in the Ordinary of the
  Mass); a unit with a letter (e.g. `incipit.33a`) has no Latin counterpart. Where the texts really
  differ, the parallel view shows a missing cell: in the Ordinary, the Italian text abridges the
  server's Confiteor (`incipit.17`–`19`), the English one adds the blessing of the incense
  (`incipit.33a`–`33b`) and lacks the first incensation.
- Texts proper to other rites (Cistercian, 1570, 1960), marked as variants in Divinum Officium, are
  left out.
- Prayers are divided into stanzas (one unit per stanza; one per line in psalmodic texts).

## Planned

- Martini Bible (Italian, 1781) and the Catechisms of Saint Pius X (1905, 1912): public domain,
  waiting for a digital source of the text.
- Ricciotti Bible: under copyright until 2034 (Giuseppe Ricciotti died in 1964); not included.
