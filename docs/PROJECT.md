# Project record

Built 11 October 2026, from a request to edit the CO2 pressure–temperature chart and cover the refrigerants used in every refrigeration system.

## The ask

Start: [https://momalley13.github.io/co2-pt/](https://momalley13.github.io/co2-pt/)

1. Make the chart work for the refrigerants used across refrigeration, not CO2 alone.
2. Rename it.
3. Keep the same instrument look: navy, teal, cream, and the same layout.
4. When a refrigerant is chosen, say how to charge a system with it.
5. Explain bubble point and dew point through the system, then show that with diagrams.
6. Put it on the iPhone home screen.

## What shipped

**Refrigerant PT**, live at [https://momalley13.github.io/](https://momalley13.github.io/).

194 refrigerants. About 80 are marked common so the picker opens on the ones a tech reaches for first. The rest are still searchable.

Groups: natural, domestic, commercial, industrial, air conditioning, automotive, chiller, ultra-low, transport, legacy.

Checked against known points before the curves were trusted:

| Check | Result |
| --- | --- |
| R-744 at −50 °C | 6.82 bar absolute, same as the original CO2 chart |
| R-134a at 40 °F | 35 psig |
| R-22 at 40 °F | about 68.5 psig |
| R-410A at 40 °F | about 118.5 psig |
| Ammonia at 20 °F | about 33.5 psig |

## How a refrigerant is chosen

The picker filters by system type. Search also hits the number, the trade name, and the composition, so "Suva", "Opteon", "XP40", or "407C" all land.

Changing refrigerant resets the coil example so superheat does not carry a nonsense pressure over from the previous fluid.

## Charging

The note under the facts is specific to the fluid on screen.

- **Pure fluid** (R-134a, R-22, R-32): weigh it. Vapor into the suction side is allowed because it cannot fractionate. The nameplate weight is still the target. Capillary systems are charge-critical.
- **Blend with glide** (R-404A, R-407C, R-448A, R-449A, R-452A): liquid only, out of an inverted cylinder or the liquid valve. Do not top off by gauge after a leak. The vapor that left is a different mix. Recover and weigh a fresh charge.
- **Near-azeotrope** (R-410A, R-507A, R-513A): still a blend, so still liquid and by weight. The glide is too small to see on the bar.
- **R-744**: by weight, not by the gauge. A warm idle vessel is already hundreds of psig. Above 31 °C the gas cooler has no bubble point and no dew point.
- **R-717**: liquid by weight, on the ammonia procedure. A flooded coil is watched by level, not by superheat.
- **A3 hydrocarbons** (R-290, R-600a, and the hydrocarbon blends): weigh in grams. Do not charge to a frost line or a gauge. Domestic cabinets are often 150 g or less.
- **A2L**: weigh to the nameplate and stay inside the charge limit for that unit and that room.
- **Low stage** (R-23, R-508B, R-14, R-170, R-1150, and the other cascade lows): charge that stage alone. Do not use the high-stage chart.

## Bubble and dew

Two pictures, both tied to the refrigerant on screen.

The loop:

- Condenser inlet is the dew point. Condenser outlet is the bubble point.
- Evaporator inlet is the bubble point. Evaporator outlet is the dew point.
- The compressor and the TXV are not saturation points.

Teal is bubble (liquid). Blue is dew (vapor). On a pure fluid both ends say "Sat" because they are the same temperature.

The bars use a real pressure from that refrigerant's curve:

- Evaporator example near 4 °C.
- Condenser example near 38 °C, pulled down if the critical point is lower.
- A pure fluid is one dot: bubble = dew, with the temperature and the pressure.
- A zeotrope shows the two temperatures and the glide in kelvin at that pressure.
- If the critical point is below 36 °C, the card says the markers disappear above it.

Superheat is measured at the evaporator outlet, from the dew point, at the outlet pressure. Subcooling is measured in the liquid line, from the bubble point, at the liquid-line pressure. Using the wrong column on a high-glide blend makes both numbers look too high.

## Where the numbers come from

Saturation curves were calculated with CoolProp's Helmholtz equations, then stored as a temperature grid in [site/data/refrigerants.json](../site/data/refrigerants.json). The phone does not call CoolProp. It interpolates the stored curve in log pressure.

- Pure fluids have one pressure array. Bubble and dew are the same.
- A zeotropic blend keeps a second array when the glide is about 0.4 K or more.
- A few legacy blends do not have published interaction parameters. Those are marked estimated in the app. Treat them as training values and confirm the OEM chart.
- Glide, GWP, safety class, trade name, and system group are stored beside the curve. Safety class follows ASHRAE 34, including A2L where that is the current class.

Pressure and temperature conversions match the original CO2 chart: 1.01325 bar atmosphere, 14.5038 psi per bar.

## What was deliberately not changed

- The original CO2 site was left up.
- The navy / teal field-tool look stayed.
- The app does not claim to replace an OEM charging chart or a nameplate.

## Publishing

The iPhone app is the static site in [site/](../site/): one HTML file, one script, the refrigerant data, and a small service worker so Add to Home Screen works offline.

That same site is what [momalley13.github.io](https://github.com/momalley13/momalley13.github.io) serves. This repository is the project copy, so the record and the app stay together even if the published site is updated later.
