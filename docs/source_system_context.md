# Source System Context and Migration Scope

This document describes the implementation context represented by the repository artifacts.

## Incumbent Source System

CardioApp was the incumbent clinical application used as the source system for the ABPM migration work. It supported cardiology-related documentation workflows and was used for 24-hour ambulatory blood pressure monitoring documentation.

For the ABPM workflow, the relevant CardioApp functions included:

- manual entry of blood pressure summary values;
- documentation of the clinical question;
- clinical assessment and interpretation;
- optional pulse wave analysis fields;
- report-oriented documentation functions;
- internal source-field identifiers used for mapping and migration analysis.

The migration work treated CardioApp as the functional and semantic starting point for the openEHR artifact. The goal was not to reproduce the old application layout, but to decide which information should be preserved as reusable clinical data, which information belonged to adjacent services, and which application-specific fields should remain outside the ABPM semantic core.

## Requirements Inputs

Requirements engineering combined clinical, application, and technical inputs:

- review of the incumbent CardioApp functionality;
- review of the source-field inventory used for ABPM documentation;
- workflow observation and clinical task analysis;
- input from the CardioApp application owner;
- clinical input from physicians and outpatient workflow personnel;
- technical input related to the target openEHR platform and possible device-interface integration.

The resulting requirements were treated as implementation requirements. They specified what the prototype had to preserve, what it could improve, and what should be assigned to surrounding production services.

## Data-Element Inventory

The source inventory contained 63 ABPM-related elements from the incumbent documentation flow. Elements were reviewed according to clinical meaning, persistence requirements, workflow visibility, and platform boundary.

The review resulted in four categories:

- ABPM template content;
- hidden semantic qualifiers or derived values;
- adjacent-service information;
- legacy or report-production artifacts.

After review, 42 elements were classified as clinical, and 27 were included in the final ABPM template. Other elements were assigned to medication, referral, reporting, distribution, or device-import services.

## Migration Boundary

The ABPM template was scoped as a focused clinical documentation artifact. The following functions were kept outside the template boundary:

- medication management and medication reconciliation;
- referral/request handling;
- automatic device import;
- report generation and distribution;
- administrative recipient and insurance information.

This boundary is part of the implementation design. It prevents the template from becoming a direct copy of the incumbent application and keeps the ABPM artifact reusable within a broader clinical data platform.

## Prototype Function Scope

The executable prototype covers the ABPM documentation core:

- structured entry of ABPM summary values;
- clinical question and assessment;
- wake and sleep context;
- measurement-count information;
- nocturnal dipping;
- optional pulse wave analysis;
- body metrics and reference-value feedback;
- persistence as an openEHR composition;
- AQL-based retrieval of previous ABPM summaries.

The prototype is a formative implementation artifact. It documents design and implementation decisions required to translate a specialty workflow into openEHR, rather than claiming routine clinical deployment.
