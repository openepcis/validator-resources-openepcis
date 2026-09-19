# OpenEPCIS DPP-Ready — RDF validator resources

Configuration and SHACL shapes behind the **OpenEPCIS Digital Product Passport
validator**, hosted by the European Commission on the shared
[Interoperability Test Bed](https://www.itb.ec.europa.eu/) as the
`openepcis` domain:

| | |
|---|---|
| Web UI | <https://www.itb.ec.europa.eu/shacl/openepcis/upload> |
| REST API | <https://www.itb.ec.europa.eu/shacl/openepcis/api> (Swagger: <https://www.itb.ec.europa.eu/shacl/swagger-ui/index.html>, domain `openepcis`) |
| SOAP API (GITB validation service) | <https://www.itb.ec.europa.eu/shacl/soap/openepcis/validation?wsdl> |

A passport is submitted as JSON-LD, Turtle, RDF/XML or N-Triples and checked
against the shapes for one validation type. `sh:Violation` fails, `sh:Warning`
and `sh:Info` are reported and tolerated — the shapes use the milder severities
deliberately, for conditional and optional data points.

## Validation types

The type id is the published contract: it is what a validation request carries
and what a Test Bed conformance statement is recorded against. Renaming one
invalidates every statement already made, so ids are stable.

| Type | Covers |
|---|---|
| `dpp.core` | OpenEPCIS DPP Core — ESPR 2024/1781 (cross-cutting) |
| `eu.battery` | EU Battery — Battery Regulation 2023/1542 |
| `eu.battery.model` | EU Battery — model granularity (EN 18223) |
| `eu.battery.batch` | EU Battery — batch granularity (EN 18223) |
| `eu.battery.item` | EU Battery — item granularity (EN 18223) |
| `eu.battery.ev` | EU Battery — electric vehicle (EC guidance coverage) |
| `eu.battery.lmt` | EU Battery — light means of transport (EC guidance coverage) |
| `eu.battery.industrial` | EU Battery — industrial (EC guidance coverage) |
| `eu.cpr` | EU Construction Products — Construction Products Regulation 2024/3110 |
| `eu.detergent` | EU Detergent — Detergents Regulation 2026/405 |
| `eu.electronics` | EU Electronics — ESPR Electronics Acts |
| `eu.eudr` | EU Deforestation — Deforestation Regulation 2023/1115 |
| `eu.iron-steel` | EU Iron & Steel — ESPR iron & steel product group (EN 10204 MTC) |
| `eu.ppwr` | EU Packaging — Packaging and Packaging Waste Regulation 2025/40 |
| `eu.textile` | EU Textile — ESPR Sustainable Textiles |
| `us.fsma204` | US FSMA 204 — FDA FSMA §204 Food Traceability Rule (21 CFR 1 Subpart S) |

Every regulation type bundles the cross-cutting DPP core shapes as well: `oec:`
obligations apply to a battery passport too. The `eu.battery.{model,batch,item}`
and `eu.battery.{ev,lmt,industrial}` variants exist because those obligations
genuinely differ by EN 18223 granularity and by battery category.

## Layout

```
resources/
├── config.properties          validation types, labels, shapes per type
└── shapes/<type>/
    ├── shapes.ttl             the constraints
    └── background.ttl         class hierarchy and code lists the shapes need
```

`background.ttl` is not decoration. `sh:class`, and the subclass resolution
behind `sh:targetClass`, are evaluated over the data graph; the validator merges
the shapes graph into the input before validating, which is what carries the
ontology across. Without it the shapes are vacuous in one direction and wrong in
the other.

Two more properties of the bundle follow from what a hosted validator cannot do
at request time, and are why it is generated rather than copied:

- **No reasoner is assumed.** Obligations stated on a superproperty are rewritten
  into plain SHACL Core alternation (`sh:alternativePath`), because nothing in
  the delivery chain applies the `rdfs:subPropertyOf` entailment the ontologies
  declare.
- **`sh:deactivated` cannot be flipped per request**, so each granularity and
  category variant ships one pre-activated copy of the shapes.

Everything is bundled locally (`validator.loadImports = false`), so a verdict
depends on the shapes alone — only the submitted document's own `@context` is
fetched.

## Generated — do not edit here

This repository is a **mirror**. The source of truth is
[openepcis/openepcis-dpp-ready](https://github.com/openepcis/openepcis-dpp-ready),
where the shapes are derived from the module ontologies and verified against the
same `isaitb/shacl-validator` image the Test Bed runs, over every reference
passport the project publishes and a deliberately broken variant of each.

Synced from openepcis-dpp-ready 0.9.9 (`b496081`) with
`pnpm run publish:validator-resources`. An edit made directly here is
overwritten by the next sync — please raise issues and pull requests against
[openepcis-dpp-ready](https://github.com/openepcis/openepcis-dpp-ready) instead.

## Licence

[Apache License 2.0](./LICENSE), as the source project.
