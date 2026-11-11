# Japan Geodesy Apps — JP-GeoConverter Pro / JP-GeoPrism / GeoDiveExa

Documentation for a family of iOS apps that handle Japan's geodetic datums (Tokyo Datum, JGD2000, JGD2011, JGD2024) and the Japan Plane Rectangular Coordinate System, for both fieldwork and learning. The source code is not published. This repository summarizes what the apps do, which coordinate systems and corrections they support, and how their accuracy is verified; detailed articles live on the official sites (in Japanese).

[日本語](README.md)

---

## Apps

| App | Description | App Store | Website |
| --- | --- | --- | --- |
| **JP-GeoConverter Pro** (formerly GeoConverter Pro) | Dedicated coordinate-conversion app. Converts between the world geodetic datums, Tokyo Datum and the Plane Rectangular systems; supports semi-dynamic correction, steady-state crustal-movement correction, and elevation via the Geoid 2011 / 2024 models. Manual input and CSV batch conversion; everything works offline | [App Store](https://apps.apple.com/app/id6761740960) | [gcpro.y42u.net](https://gcpro.y42u.net/) |
| **JP-GeoPrism** | Learning app that visualizes datum shifts and the geoid on maps and heatmaps, with quizzes | [App Store](https://apps.apple.com/app/id6780149823) | [gmp.y42u.net](https://gmp.y42u.net/) |
| **GeoDiveExa** | High-precision RTK-GNSS survey app, and the origin of the coordinate-conversion engine | — | [y42u.net/tec001](https://y42u.net/tec001/) |

> The names shown on the App Store switch over with the next update that includes the November 2026 renaming. App Store IDs and links do not change.

---

## Contents

| Page | Description |
| --- | --- |
| [geoconverter-pro/README.md](geoconverter-pro/README.md) | JP-GeoConverter Pro: overview, supported systems, how the corrections work, 10 FAQs, related articles (Japanese) |
| [geoconverter-pro/supported-systems.md](geoconverter-pro/supported-systems.md) | Tables of supported datums, coordinate systems, corrections and built-in parameter files (Japanese) |
| [glossary.md](glossary.md) | Glossary of geodetic and coordinate-system terms, 30 entries (Japanese) |
| geoprism-jp/ | JP-GeoPrism: overview, list of visualizations, FAQ (coming soon) |
| geodiveexa/ | GeoDiveExa: overview, RTK-GNSS support (coming soon) |
| geocore/ | The shared engine GeoCoreJP (coming soon) |

---

## The shared engine: GeoCoreJP

JP-GeoConverter Pro and JP-GeoPrism share **GeoCoreJP**, a Swift Package extracted from GeoDiveExa. GeoCoreJP computes the Tokyo Datum ⇄ JGD2000 transformation (TKY2JGD), coordinate corrections for earthquakes since 2003 (jgdMerge2011 / 2024), semi-dynamic correction (SemiDyna), steady-state crustal-movement correction (pos2jgd), conversion between latitude/longitude and the Plane Rectangular systems zones 1–19, and ellipsoidal-height ⇄ elevation conversion with the Geoid 2011 / 2024 models. The parameter files published by the Geospatial Information Authority of Japan (GSI) are bundled, so every calculation completes on the device. Accuracy is verified by comparing every test point against GSI's official tools (TKY2JGD, PatchJGD, SemiDynaEXE, POS2JGD) — see the [verification article](https://gcpro.y42u.net/2026/06/17/gsi-coordinate-validation/) (Japanese).

- [Design principles behind GeoCoreJP's precision](https://gcpro.y42u.net/2026/06/03/geocore-precision-design/) (Japanese)
- [What PROJ covers and what it doesn't — why a Japan-specific engine](https://gcpro.y42u.net/2026/07/09/proj-geocore-comparison/) (Japanese)

---

## Books

For an end-to-end read on why Japan's coordinates shift and how to handle them in practice, see the Kindle series *Understanding Japan's Geodetic Systems* (in Japanese, 3 volumes): [vol. 1](https://www.amazon.co.jp/dp/B0H971W8WX), [Implementation](https://www.amazon.co.jp/dp/B0H97LPNH3), [Q&A](https://www.amazon.co.jp/dp/B0HF4SJC1L). All are Kindle Unlimited eligible.

---

## Developer

Apps, Kindle books and public projects are listed at [GitHub: amru195704](https://github.com/amru195704).
