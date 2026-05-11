# Artifact Inventory

This document summarizes the main artifacts in the repository and explains how they relate to the ABPM implementation.

## Template Exports

### ABPM Template

Path:

`template-exports/outpatient-24h-blood-pressure-monitoring.v0/`

Key files:

- `Templates/outpatient-24h-blood-pressure-monitoring.v0.opt`
- `Templates/outpatient-24h-blood-pressure-monitoring.v0.t.json`
- `manifest.json`
- `Archetypes/*.adl`

Purpose:

The ABPM template is the main semantic artifact. It represents outpatient 24-hour blood pressure monitoring as an openEHR encounter and brings together blood pressure summaries, temporal context, quality-related counts, pulse-related values, optional pulse wave analysis, and clinical context.

### Service Request Template

Path:

`template-exports/outpatient-service-request/`

Key files:

- `Templates/outpatient-service-request.opt`
- `Templates/outpatient-service-request.t.json`
- `Archetypes/openEHR-EHR-INSTRUCTION.service_request.v1.adl`
- `Archetypes/openEHR-EHR-COMPOSITION.request.v1.adl`

Purpose:

This template separates request/referral concepts from the ABPM documentation artifact. It is included because the implementation deliberately kept the ABPM clinical core distinct from surrounding workflow services.

## Prototype Export

Path:

`prototype/24h_bp_monitoring_test_1_0_104_FORM/`

Key files:

- `24h_bp_monitoring_test_1_0_104_FORM.zip`
- `24h_bp_monitoring_test_1_0_104_FORM/manifest.json`
- `24h_bp_monitoring_test_1_0_104_FORM/form-*`
- `24h_bp_monitoring_test_1_0_104_FORM/summary-*`
- `24h_blood_pressure_values_VIEW.json`
- `24h_bp_js_version_VIEW.json`

Purpose:

The prototype export demonstrates how the ABPM template was made executable in Better Studio. It includes form pages, layout configuration, conditional behavior, widget configuration, and AQL-based views.

## API Collection

Path:

`postman/openEHR APIs.postman_collection.json`

Purpose:

The Postman collection contains example requests for interacting with an openEHR REST API during development. It is intended for authorized development environments only and does not include production credentials.

## CKM Bulk Export

Path:

`archetypes-ckm-bulk-export/`

Purpose:

The archive contains archetypes exported from the openEHR Clinical Knowledge Manager during modeling work. It is kept to document the modeling context and to support inspection of the archetype basis used during development.
