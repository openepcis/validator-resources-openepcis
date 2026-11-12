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
| `x.cirpass2-battery-0.3.0.profile` | CIRPASS-2 Battery 0.3.0 (draft release), battery passport profile (with carbon footprint) (CIRPASS-2; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.cirpass2-battery-0.3.0.view-authorities` | CIRPASS-2 Battery 0.3.0 (draft release), view for authorities (CIRPASS-2; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.cirpass2-battery-0.3.0.view-legitimate-interest` | CIRPASS-2 Battery 0.3.0 (draft release), view for persons with a legitimate interest (CIRPASS-2; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.cirpass2-battery-0.3.0.view-public` | CIRPASS-2 Battery 0.3.0 (draft release), public view (CIRPASS-2; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.cirpass2-textile-2.0.0.product` | CIRPASS-2 Textile 2.0.0, textile product data (quantitative, recyclability and substances-of-concern shapes) (CIRPASS-2; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.epcis-2.0.1.document` | GS1 EPCIS / CBV 2.0.1, EPCIS document (JSON Schema and SHACL) (GS1; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.core` | EU DPP Registry semantic data artifacts 1.0.0, core passport (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.batteries.pub` | EU DPP Registry semantic data artifacts 1.0.0, batteries, view pub (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.batteries.res1` | EU DPP Registry semantic data artifacts 1.0.0, batteries, view res1 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.batteries.res2` | EU DPP Registry semantic data artifacts 1.0.0, batteries, view res2 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.batteries.res3` | EU DPP Registry semantic data artifacts 1.0.0, batteries, view res3 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.evb.pub` | EU DPP Registry semantic data artifacts 1.0.0, batteries, EV subgroup, view pub (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.evb.res1` | EU DPP Registry semantic data artifacts 1.0.0, batteries, EV subgroup, view res1 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.evb.res2` | EU DPP Registry semantic data artifacts 1.0.0, batteries, EV subgroup, view res2 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.evb.res3` | EU DPP Registry semantic data artifacts 1.0.0, batteries, EV subgroup, view res3 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.ind.pub` | EU DPP Registry semantic data artifacts 1.0.0, batteries, industrial subgroup, view pub (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.ind.res1` | EU DPP Registry semantic data artifacts 1.0.0, batteries, industrial subgroup, view res1 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.ind.res2` | EU DPP Registry semantic data artifacts 1.0.0, batteries, industrial subgroup, view res2 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.ind.res3` | EU DPP Registry semantic data artifacts 1.0.0, batteries, industrial subgroup, view res3 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.lmt.pub` | EU DPP Registry semantic data artifacts 1.0.0, batteries, LMT subgroup, view pub (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.lmt.res1` | EU DPP Registry semantic data artifacts 1.0.0, batteries, LMT subgroup, view res1 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.lmt.res2` | EU DPP Registry semantic data artifacts 1.0.0, batteries, LMT subgroup, view res2 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.eu-dpp-1.0.0.lmt.res3` | EU DPP Registry semantic data artifacts 1.0.0, batteries, LMT subgroup, view res3 (European Commission; hosted by OpenEPCIS, not endorsed by the publisher) |
| `x.keystone-v3.dpp` | DPP Keystone v3, passport (core schema and every sector schema, which apply by contentSpecificationIds; SHACL generated from the ontology) (DPP Keystone (dpp-keystone.org); hosted by OpenEPCIS, not endorsed by the publisher) |

Every regulation type bundles the cross-cutting DPP core shapes as well: `oec:`
obligations apply to a battery passport too. The `eu.battery.{model,batch,item}`
and `eu.battery.{ev,lmt,industrial}` variants exist because those obligations
genuinely differ by EN 18223 granularity and by battery category.

## External models

Besides the OpenEPCIS types, the validator hosts types for external DPP models at a pinned release
(type id `x.<model>-<version>.<scope>`), so a conformance statement always names the release it
was made against. The publisher's SHACL shapes and JSON Schemas are bundled byte for byte under
`resources/artifacts/` and `json-resources/artifacts/`; OpenEPCIS adds one presence shape per
SHACL type and nothing else. Hosting does not imply endorsement by the publisher.

- BatteryPass-Ready consortium (GEFEG); schemas derived by OpenEPCIS, BatteryPass-Ready upload format 1.3 (derived from the live GEFEG validator) 1.3 (retrieved 2026-06-17, SHA-256 per file, https://batterypass-ready.gefeg.com/automation-console/api/ValidateJSON (live required-sets, probed)), licence https://creativecommons.org/licenses/by/4.0/
- BatteryPass-Ready consortium (GEFEG), BatteryPass-Ready data model 2.0.1 (commit 64761a79, https://git.gefeg.com/bp/BatteryPassDataModel), licence https://creativecommons.org/licenses/by/4.0/
- Battery Pass Consortium, Battery Pass Consortium data model (SAMM) 1.2 (commit 7f409181, https://github.com/batterypass/BatteryPassDataModel), licence https://creativecommons.org/licenses/by/4.0/
- Catena-X (Eclipse Tractus-X), Catena-X battery pass aspect model (SAMM) 6.1.0 (commit 46b4def7, https://github.com/eclipse-tractusx/sldt-semantic-models), licence https://creativecommons.org/licenses/by/4.0/
- CIRPASS-2, CIRPASS-2 Battery 0.3.0 (draft release) (commit c8e58474, https://github.com/CIRPASS-2/ontologies-battery), licence https://www.apache.org/licenses/LICENSE-2.0
- CIRPASS-2, CIRPASS-2 Textile 2.0.0 (commit ff8a429f, https://github.com/CIRPASS-2/ontologies-docs), licence https://creativecommons.org/licenses/by/4.0/
- GS1, GS1 EPCIS / CBV 2.0.1 (commit 6f714682, https://github.com/gs1/EPCIS), licence https://www.gs1.org/standards/ip (treated as freely redistributable, see vendor/gs1-epcis/README.md)
- European Commission, EU DPP Registry semantic data artifacts 1.0.0 (archive sha256 46b753cdcdf1, https://single-market-economy.ec.europa.eu/document/download/5fad8a3a-9c18-486d-be02-01eb540e91e8_en?filename=DPP%20Registry%20%E2%80%93%20Semantic%20Data%20Artifacts.zip), licence https://interoperable-europe.ec.europa.eu/collection/eupl/eupl-text-eupl-12
- DPP Keystone (dpp-keystone.org), DPP Keystone v3 (commit 4d9bd0c9, https://github.com/dpp-keystone-org/DPPKeystoneOrg), licence https://creativecommons.org/publicdomain/zero/1.0/
- UN/CEFACT (UNTP), UN Transparency Protocol 0.7.0 (retrieved 2026-11-12, SHA-256 per file, https://untp.unece.org/artefacts/schema/v0.7.0/), licence https://creativecommons.org/licenses/by/4.0/
- UN/CEFACT (UNTP), UN Transparency Protocol 0.8.0 (retrieved 2026-11-12, SHA-256 per file, https://untp.unece.org/artefacts/schema/v0.8.0/), licence https://creativecommons.org/licenses/by/4.0/

What each type was checked with, and the verdict on every example, is
[docs/conformance/INTEROP_CONFORMANCE.md](https://github.com/openepcis/openepcis-dpp-ready/blob/main/docs/conformance/INTEROP_CONFORMANCE.md)
of the source project.

## Layout

```
resources/                     RDF validator domain (read by the Test Bed)
├── config.properties          validation types, labels, shapes per type
├── shapes/<type>/
│   ├── shapes.ttl             the constraints
│   └── background.ttl         class hierarchy and code lists the shapes need
└── artifacts/<model>-<version>/   an external model's shapes, verbatim
json-resources/                JSON validator domain (isaitb/json-validator)
├── config.properties
└── artifacts/<model>-<version>/   an external model's JSON Schemas, verbatim
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

Synced from openepcis-dpp-ready 0.14.0 (`d765844f`) with
`pnpm run publish:validator-resources`. An edit made directly here is
overwritten by the next sync — please raise issues and pull requests against
[openepcis-dpp-ready](https://github.com/openepcis/openepcis-dpp-ready) instead.

## Licence

[Apache License 2.0](./LICENSE), as the source project, except the external models' artifacts
under `resources/artifacts/` and `json-resources/artifacts/`, which keep the licence of their
publisher listed under "External models".
