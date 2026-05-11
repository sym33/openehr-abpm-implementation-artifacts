# openEHR ABPM Implementation Artifacts

This repository contains implementation artifacts for an openEHR-based documentation prototype for outpatient 24-hour ambulatory blood pressure monitoring (ABPM). The artifacts support reuse, inspection, and discussion of the design decisions described in the accompanying manuscript.

The project focuses on the translation of a specialty documentation workflow into an openEHR-based structure. It includes the ABPM template, local archetype extensions, a Better Studio prototype export, and API material for working with openEHR compositions.

## Repository Scope

This repository is an artifact package, not a standalone clinical product. It is intended for:

- reviewing the openEHR template structure for ABPM documentation;
- inspecting how ABPM concepts were represented with existing archetypes, constrained events, and local clusters;
- reproducing the prototype import in a compatible Better Studio environment;
- examining AQL-based reuse concepts for longitudinal ABPM summaries;
- supporting peer review of the associated implementation paper.

It does not contain patient data, production credentials, or institution-specific operational configuration.

## Contents

| Path | Purpose |
| --- | --- |
| `template-exports/outpatient-24h-blood-pressure-monitoring.v0/` | Main openEHR ABPM template export with the template files and referenced archetypes. |
| `template-exports/outpatient-service-request/` | Service request template used to separate request/referral concepts from the ABPM documentation core. |
| `prototype/24h_bp_monitoring_test_1_0_104_FORM/` | Better Studio form and AQL widget export for the executable prototype. |
| `postman/openEHR APIs.postman_collection.json` | Postman collection for interacting with an openEHR REST API during development and testing. |
| `archetypes-ckm-bulk-export/` | CKM archetype bulk export used during modeling work. |
| `docs/artifact_inventory.md` | More detailed description of the repository artifacts. |
| `docs/source_system_context.md` | Description of the incumbent source system, requirements inputs, and migration scope. |
| `docs/import_notes.md` | Practical notes for importing and inspecting the artifacts. |
| `docs/modeling_notes.md` | Summary of the main modeling and implementation design decisions. |

## Main Artifact

The central artifact is the ABPM template:

`template-exports/outpatient-24h-blood-pressure-monitoring.v0/Templates/outpatient-24h-blood-pressure-monitoring.v0.opt`

The same template is also available as a JSON web-template export:

`template-exports/outpatient-24h-blood-pressure-monitoring.v0/Templates/outpatient-24h-blood-pressure-monitoring.v0.t.json`

The template represents ABPM documentation as an encounter-oriented openEHR artifact. It covers ABPM summary values, wake and sleep context, measurement counts, nocturnal dipping, pulse-related values, optional pulse wave analysis, reason for encounter, and clinical interpretation support.

## Prototype Export

The Better Studio export is located under:

`prototype/24h_bp_monitoring_test_1_0_104_FORM/`

It includes:

- the form package and manifest;
- form descriptions and layouts;
- AQL widget configuration;
- JavaScript resources used by Better Studio widgets;
- the matching ABPM template file used by the form export.

The prototype demonstrates how the semantic template can be translated into a task-oriented interface with hidden semantic qualifiers, derived values, conditional display logic, and query-based longitudinal views.

## Design Principles

The artifacts follow four practical design principles:

1. **Preserve clinical meaning before preserving legacy layout.** Legacy fields were triaged according to clinical meaning, persistence needs, workflow visibility, and module boundary.
2. **Keep the ABPM template focused.** Medication, referral, device import, reporting, and distribution were treated as adjacent services rather than embedded in the ABPM documentation core.
3. **Persist context needed for reuse.** Hidden qualifiers such as sleep state, interval width, and mathematical function were retained where required for later interpretation and AQL retrieval.
4. **Separate modeling from interface behavior.** Archetype/template decisions, Better Studio form behavior, and platform integration tasks are documented as distinct implementation concerns.

## How to Inspect the Artifacts

1. Review the OPT or web-template export in `template-exports/outpatient-24h-blood-pressure-monitoring.v0/Templates/`.
2. Inspect local cluster archetypes for ABPM-specific extensions in `template-exports/outpatient-24h-blood-pressure-monitoring.v0/Archetypes/`.
3. Import the Better Studio package from `prototype/24h_bp_monitoring_test_1_0_104_FORM/` into a compatible Better Studio environment.
4. Use the Postman collection only with a local or authorized openEHR REST endpoint.

See `docs/import_notes.md` for additional practical details.

## Limitations

The prototype export depends on Better Studio and is not a standalone web application. The artifacts are provided for review, reuse, and implementation planning. Before clinical deployment, a local team would still need production integration, access control, device interfaces, report generation, validation, and usability testing in the target environment.

## Citation

If you use this repository, cite it as a software and implementation artifact repository. A machine-readable citation file is provided in `CITATION.cff`.

## License

This repository is released under the MIT License. See `LICENSE` for details. Reused CKM archetypes and third-party exports may carry their own attribution and governance requirements from their respective sources.
