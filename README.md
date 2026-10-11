# Refrigerant PT

A field chart for the refrigerants used in real systems: domestic, commercial, industrial, air conditioning, automotive, chillers, ultra-low and cascade, transport, and the legacy stuff still in service.

It started as a CO2-only pressure–temperature chart and grew, in one build, into a chart for 194 refrigerants, with a charging method and bubble/dew diagrams that follow whichever fluid you pick.

**Open the app:** [https://momalley13.github.io/](https://momalley13.github.io/)

The original CO2 chart is still there: [https://momalley13.github.io/co2-pt/](https://momalley13.github.io/co2-pt/)

Training values. The nameplate and the OEM chart win.

## On an iPhone

1. Open [https://momalley13.github.io/](https://momalley13.github.io/) in Safari.
2. Tap Share.
3. Tap **Add to Home Screen**.
4. Tap **Add**.

The icon opens full screen. After the first load it works offline.

## What you can do

- Look up saturation pressure from temperature, or temperature from pressure.
- Switch °C / °F and bar, psig, psia, kPa.
- See the curve, including a separate dew line when the blend has glide.
- Check superheat and subcooling on the coil tab. Dew point for superheat, bubble point for subcooling.
- Read safety class, GWP, trade name, boiling point, critical point, and standstill pressure.
- Filter by the kind of system, or search a trade name.
- Read how to charge that specific refrigerant.
- See where bubble point and dew point sit on the loop, and the temperature gap at one real pressure.

## This repository

| Path | What it is |
| --- | --- |
| [site/](site/) | The installable app, as published |
| [docs/PROJECT.md](docs/PROJECT.md) | The project record: what was asked, what was decided, how the numbers work |

The live site is published from [momalley13/momalley13.github.io](https://github.com/momalley13/momalley13.github.io). This repository is the project: the app plus the record of how it was built.

## Related

- [co2-pt](https://github.com/momalley13/co2-pt) — the original CO2 chart
- [co2-cascade](https://github.com/momalley13/co2-cascade)
- [co2-refrigeration-training](https://github.com/momalley13/co2-refrigeration-training)
