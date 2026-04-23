# BACnet

## Standard Metrics Catalog

[`bacnet_standard_metrics.json`](./bacnet_standard_metrics.json) lists every
standardized metric defined by the BACnet `BACnetEngineeringUnits`
enumeration (ANSI/ASHRAE Standard 135). Each entry exposes the canonical
unit name, the numeric enumeration value used on the wire as the `Units`
property of analog objects, the unit symbol, the engineering category, the
encoded data type (`REAL` — 32-bit IEEE 754, the type of `Present_Value`
for analog objects), and a Sparkplug B data-type mapping. The schema is
modelled on the KNX DPT catalog so the file can be consumed by the same
tooling.

### Entry schema

| Field | Description |
| --- | --- |
| `metric_id` / `metric_number` | BACnet engineering-unit enumeration value (string and integer forms). |
| `name` | Canonical hyphenated BACnet unit name (e.g. `degrees-celsius`). |
| `enum_name` | C-style enum identifier (e.g. `UNITS_DEGREES_CELSIUS`). |
| `display_name` | Human-friendly label. |
| `description` | Short description of the quantity. |
| `unit` | Unit symbol (e.g. `°C`, `kWh`, `m³/h`). |
| `category` | Grouping (`temperature`, `electrical`, `energy`, …). |
| `data_type`, `encoding`, `size_bits`, `size_bytes` | Wire encoding of the carried value. |
| `value_min`, `value_max`, `resolution` | Range of the carried `REAL` value. |
| `sparkplug_data_type` / `sparkplug_data_type_value` | Sparkplug B mapping. |
| `bacnet_object_types`, `bacnet_property` | Where the metric is typically reported. |
| `value_conversion` | UI ↔ bus conversion formulas. |

Reserved and proprietary range markers from the enumeration are omitted —
only standardized metrics are listed.