# Import Notes

The artifacts in this repository can be inspected without running a clinical system. Executing the prototype requires a compatible Better Studio environment and an authorized openEHR backend.

## Inspecting the Template

Use the OPT or web-template export in:

`template-exports/outpatient-24h-blood-pressure-monitoring.v0/Templates/`

The ADL files in the adjacent `Archetypes/` directory include the archetypes referenced by the template. Local ABPM-specific clusters are included where no suitable reusable archetype covered the required concept.

## Importing the Better Studio Prototype

The Better Studio export is located in:

`prototype/24h_bp_monitoring_test_1_0_104_FORM/`

Use the ZIP package or the unpacked export directory, depending on the import workflow supported by your Better Studio version.

Expected prerequisites:

- access to Better Studio;
- an openEHR-compatible backend configured for the target environment;
- the ABPM template available in the target environment;
- appropriate permissions to import form and widget resources.

The prototype export is not a standalone web application. It depends on Better Studio runtime behavior, including form rendering, dependencies, custom scripts, and widget execution.

## Using the Postman Collection

The Postman collection is provided for development and testing:

`postman/openEHR APIs.postman_collection.json`

Before using it, configure endpoint URLs, authentication, and environment variables for your own authorized openEHR backend. The repository does not provide production credentials.

## Common Checks

After import, check that:

- the ABPM template can be loaded by the form;
- form pages render in the intended task order;
- conditional pulse wave analysis fields can be shown and hidden;
- calculated or derived values are persisted where expected;
- AQL widgets can retrieve stored ABPM summaries;
- no patient-identifying data are present in test compositions.
