# Modeling Notes

This document summarizes the main modeling choices represented by the repository artifacts.

## Encounter-Oriented Composition

The ABPM artifact uses an encounter-oriented structure because the documentation combines device-derived measurements, patient protocol information, clinical questioning, and professional interpretation. This choice avoids treating ABPM as a simple static report and keeps the clinical context explicit.

## Blood Pressure Summaries

The blood pressure archetype is used as the core structure for systolic and diastolic values. ABPM required multiple clinically distinct summary contexts, including 24-hour, daytime, and nighttime values. These contexts require explicit temporal and state qualifiers so that later interpretation does not depend on form layout alone.

## Wake and Sleep Context

Wake and sleep periods are clinically important for ABPM interpretation. The implementation therefore stores relevant context for downstream query and reuse, rather than leaving it as text-only documentation.

## Measurement Counts and Data Quality

Measurement counts were modeled because they affect confidence in ABPM summaries. A mean value derived from few successful measurements is not equivalent to the same value derived from a complete recording.

## Pulse Wave Analysis

Pulse wave analysis was represented as an optional specialty component. Local clusters were used for ABPM-specific pulse wave analysis outputs where existing reusable archetypes did not provide the required structure.

## Clinical Question and Interpretation

The clinical question is represented as part of the ABPM encounter context. Interpretation is treated as clinically authored content rather than as a derived technical artifact.

## Adjacent Services

The model keeps several concerns outside the ABPM documentation core:

- medication management;
- referral and request handling;
- automated device import;
- report generation;
- document distribution.

This boundary prevents the template from reproducing the incumbent application as a new silo. It also makes the ABPM artifact easier to reuse in a broader hospital data platform.

## Interface Behavior

The Better Studio prototype uses form dependencies, custom scripts, internal variables, hidden fields, and AQL widgets. These mechanisms are implementation choices for making the semantic model usable in a clinical interface; they are intentionally distinct from the openEHR modeling decisions.
