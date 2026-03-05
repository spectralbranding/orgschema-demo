# Spectra Coffee

A complete coffee shop business specified entirely as configuration.

Spectra Coffee is a reference implementation of the [Organizational Schema Theory](https://github.com/spectralbranding/orgschema-framework) framework. It demonstrates that an entire business — products, brand identity, compliance, pricing, nutrition, allergens — can be described as machine-readable, version-controlled YAML specifications with no ambiguity and no prose-only documentation.

Every measurement is in SI units. Every margin is computed from itemized costs. Every allergen is traced to its source ingredient and cross-contamination pathway. Every regulatory classification is derived from raw values against jurisdiction-specific thresholds. The entire business is a diff.

## Why a coffee shop

A coffee shop is the right scale for a schema-configured demo:

- **Simple enough to be schematic.** 6 products, 3 roles, 1 location. The full spec fits in a single repository without becoming overwhelming.
- **Tangible and relatable.** Everyone understands espresso, milk, and croissants. No domain expertise required to evaluate the specs.
- **Clear process variety.** Equipment-operated (espresso extraction), human-executed (latte art), hybrid (par-baked croissant finishing), and regulatory (HACCP monitoring) processes coexist in one operation.
- **Visible brand signals.** A physical space with lighting, music, temperature, packaging, and signage provides a rich signal surface for demonstrating the SBT connection.
- **Regulatory surface.** Food safety (HACCP/ISO 22000), allergen management (EU 1169/2011), nutritional labeling, and multi-jurisdiction classification rules all apply.
- **Multiple observer types.** Morning regulars, first-time visitors, delivery app users, and food inspectors all perceive the same operation through radically different filters.

## Repository structure

```
orgschema-demo/
  organization.yaml           # Identity layer: name, mission, values, location, roles
  brand/
    identity.yaml              # Visual identity, packaging, environment (lighting, music, temperature)
  products/
    espresso.yaml              # Espresso spec: grind, dose, extraction params, nutrition, COGS
    americano.yaml             # Americano spec: espresso-to-water ratio, serving temps, nutrition
    cappuccino.yaml            # Cappuccino spec: milk steaming, foam depth, allergens
    filter_coffee.yaml         # Filter coffee spec: brew ratio, grind size, contact time, nutrition
    oat_latte.yaml             # Oat latte spec: plant-milk default, modifiers, cross-refs
    croissant.yaml             # Croissant spec: par-bake finishing, storage, discard policy
  processes/
    opening_closing.yaml       # Daily open/close checklists with responsible roles and timing
    quality_control.yaml       # Calibration, tasting, visual/weight checks, NCR procedure
    equipment_maintenance.yaml # Preventive maintenance schedules, cleaning, descaling, replacement
    internal_communications.yaml # Meeting formats, tone of voice, andon, kaizen, incident comms
  compliance/
    food_safety.yaml           # HACCP plan: 5 CCPs, prerequisite programs, corrective actions
    allergen_management.yaml   # EU 14 allergens: inventory, cross-contamination matrix, training
  signals/
    signal-map.yaml            # SBT connection: 19 config-to-dimension mappings
    observer-profiles.yaml     # 4 observer types with spectral weights and sensitivity profiles
  layers/
    classifications.yaml       # Multi-jurisdiction regulatory thresholds (EU, US FDA, UK, Codex)
```

## How to read this

The repository is organized in layers, each building on the one below:

**Identity layer** -- `organization.yaml` defines who Spectra Coffee is: name, mission, values, location, operating hours, and roles. Every other file in the repository must be consistent with these declarations.

**Brand layer** -- `brand/identity.yaml` specifies visual identity (colors, typography, logo variants), packaging (cup sizes in ml, bag dimensions in mm), and the physical environment (temperature targets in Celsius, lighting schedules in Kelvin and percent, music genres with max dB by time period). The environment section treats ambiance as infrastructure, not vibes.

**Product layer** -- `products/` contains fully quantitative product specifications. Each file declares preparation steps with measurable parameters (grind particle size in micrometers, extraction pressure in bar, foam depth in millimeters), ingredient composition with supplier data and per-serving costs, nutrition computed from ingredient composition (not preset values), allergens traced to source ingredients, itemized COGS, and pricing with computed margins. Products cross-reference each other: the oat latte references `products/espresso.yaml` for its espresso base.

**Compliance layer** -- `compliance/` implements continuous certification. `food_safety.yaml` is a complete HACCP plan with 5 critical control points, each specifying the hazard, monitoring method, critical limits, corrective actions, and telemetry sources. `allergen_management.yaml` consolidates allergen data from all products into an inventory, defines a cross-contamination matrix for shared equipment, and specifies staff training requirements and customer communication protocols.

**Process layer** -- `processes/` specifies operational procedures: opening/closing checklists, quality control (calibration, tasting, visual/weight checks, NCR procedure), equipment maintenance (preventive schedules, cleaning, descaling, replacement intervals), and internal communications (TPS-integrated meeting formats, tone of voice, andon, kaizen, incident reporting).

**Signal layer** -- `signals/` connects operational configuration to Spectral Brand Theory. `signal-map.yaml` identifies 19 configuration values that emit brand signals across 8 spectral dimensions, distinguishing designed signals (intentional) from ambient signals (emergent from operations). `observer-profiles.yaml` models 4 perceiver types with different spectral weights and sensitivity profiles.

**Classification layer** -- `layers/classifications.yaml` defines regulatory thresholds for nutritional claims (fat-free, low-fat, sugar-free, low-sugar) across 4 jurisdictions (EU, US FDA, UK, Codex Alimentarius). Products are classified by computing their nutritional values against these thresholds, not by manual labeling.

## Design principles

**Every measurement in SI units.** Grams, milliliters, seconds, degrees Celsius, bar, micrometers, millimeters, decibels, Kelvin. No "pumps", "scoops", "dashes", "a pinch of", or "until golden." A specification that cannot be measured cannot be verified.

**Nutrition computed from composition.** Each ingredient declares nutrition per 100ml or per 100g. Serving nutrition is computed by multiplying ingredient quantities by their per-unit nutrition values. The computation is shown in comments so it can be audited.

**COGS itemized and margins computed.** Every product lists per-serving cost for each ingredient and consumable. Total COGS, price, and margin percentage are declared together. Changing a supplier cost propagates visibly through the margin calculation.

**Allergens declared from ingredients.** Declared allergens trace directly to source ingredients. Cross-contamination risks trace to shared equipment with specified mitigation procedures. The cross-contamination matrix in `compliance/allergen_management.yaml` maps every shared equipment item to the allergen transfer risk it creates.

**Classifications computed from raw values.** A product is "low-fat" or "sugar-free" not because someone labeled it that way, but because its computed nutritional values fall below the threshold defined in `layers/classifications.yaml` for the relevant jurisdiction. Change the recipe and the classification changes automatically.

**IaC lineage.** This approach borrows from Infrastructure as Code (IaC) practices in software engineering -- Terraform, Ansible, Kubernetes manifests -- and extends them from IT infrastructure to business operations.

**Version controlled.** Every change is a diff. Adding a new product is an addition. Changing a recipe is a modification with a visible before-and-after. Removing an allergen declaration is a deletion that triggers review. The repository is the single source of truth.

## The SBT connection

Process configurations are signal sources in [Spectral Brand Theory](https://github.com/spectralbranding/sbt-framework) (Zharnikov 2026a). Every operational parameter — from extraction temperature to music genre to discard policy — emits a brand signal that observers perceive through their particular spectral filters.

The `signals/signal-map.yaml` file makes this connection explicit with 19 mappings across all 8 spectral dimensions: semiotic, narrative, temporal, ideological, economic, experiential, cultural, and social. Each mapping identifies the source configuration value, the SBT dimension it activates, whether the emission is designed or ambient, and a description of the signal.

The `signals/observer-profiles.yaml` file models how different observer types weight these dimensions. A morning regular allocates 0.9 attention to temporal signals (rhythm and routine) but only 0.2 to narrative (the origin story was absorbed long ago). A food inspector allocates 0.0 to narrative and economic but responds with extreme sensitivity to any negative compliance signal.

The implication: the same YAML files that run the business also describe its brand. Configuration is not separate from brand — configuration _is_ brand.

## Fork this

To adapt Spectra Coffee for a different business:

1. **Change identity.** Edit `organization.yaml` with your business name, mission, values, and location.
2. **Swap products.** Replace the files in `products/` with your own product specifications. Follow the same structure: preparation steps with measurable parameters, ingredients with per-serving costs, computed nutrition, and allergen declarations.
3. **Adjust brand.** Edit `brand/identity.yaml` with your colors, typography, packaging specs, and environment parameters.
4. **Adapt compliance.** Modify `compliance/` for your regulatory context. The HACCP plan structure applies to any food service business; adjust critical control points for your specific hazards.
5. **Update classifications.** If your products need different regulatory classifications, adjust the thresholds in `layers/classifications.yaml` or add jurisdiction-specific rules.
6. **Map your signals.** Use `signals/signal-map.yaml` as a template to identify which of your configuration values emit brand signals and across which SBT dimensions.

## Limitations

This demo specifies the codifiable surface of a business, not the entire business. Areas intentionally outside scope:

- Staff scheduling and labor planning
- Financial reporting and P&L
- Supplier negotiation strategy
- Customer acquisition and marketing
- Interior design beyond color/temperature/lighting parameters
- COGS figures exclude labor cost (ingredient-only margins)
- Observer profile spectral weights are illustrative, not empirically calibrated

## Related projects

- [spectralbranding/orgschema-framework](https://github.com/spectralbranding/orgschema-framework) -- Framework and methodology for schema-configured organizations
- [spectralbranding/sbt-framework](https://github.com/spectralbranding/sbt-framework) -- Spectral Brand Theory: the theoretical framework
- [spectralbranding/sbt-papers](https://github.com/spectralbranding/sbt-papers) -- Academic papers on SBT

## License

MIT
