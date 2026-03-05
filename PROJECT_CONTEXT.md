# Config-Org Demo - Project Context

**Type**: Reference implementation (Spectra Coffee -- a coffee shop specified as configuration)
**Status**: Session 1 COMPLETE. 17 YAML + 5 perception YAML + dissemination channels.
**Created**: 2026-03-04

---

## What This Project Is

Spectra Coffee is a reference implementation of the Organizational Schema Theory methodology. An entire coffee shop -- products, brand identity, compliance, pricing, nutrition, allergens, processes -- specified as machine-readable, version-controlled YAML with no ambiguity and no prose-only documentation.

## Repository Structure

```
orgschema-demo/
├── organization.yaml           Identity layer
├── brand/identity.yaml         Visual identity, packaging, environment
├── products/                   6 items (espresso, oat_latte, cappuccino, croissant, filter_coffee, americano)
├── processes/                  4 files (internal_comms, opening_closing, quality_control, equipment_maintenance)
├── compliance/                 food_safety (HACCP), allergen_management
├── signals/                    signal-map (19 mappings, 8 SBT dimensions), observer-profiles (4 types)
├── layers/classifications.yaml Multi-jurisdiction regulatory thresholds
├── perception/                 5 YAML files (experience contract, spectral profile, cohort analysis, convergence, executor swap)
│   └── dissemination_channels.yaml  Signal dissemination layer (SBT v2.2)
└── README.md
```

## Key Facts

- **All SI units**: grams, millilitres, seconds, Celsius
- **Designed/ambient ratio**: 0.70 (70% designed signals)
- **Coherence type**: Signal coherence (all cohorts perceive consistent core)
- **4 observer types**: morning regular, weekend explorer, delivery app user, food inspector
- **Config format**: YAML for specs, JSON for computed outputs

## Related

- Development workspace: `viberesearch/orgschema` (private)
- Framework repo: `spectralbranding/orgschema-framework` (public)
- SBT framework: `spectralbranding/sbt-framework` (public)
