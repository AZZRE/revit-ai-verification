# Revit AI Verification

**AI proposes. Engineers approve. The system verifies.**

A verification-first engineering automation prototype for Autodesk Revit. Natural-language requests become constrained action proposals, followed by deterministic checks, explicit engineer approval and model read-back verification.

Developed for Revit 2024 on Windows using C#, .NET Framework 4.8, WPF and local LLM inference through Ollama. This is an engineering portfolio, not a production-readiness or certification claim.

## 1. Engineering Problem

A correctly interpreted sentence does not establish that a BIM change is valid, authorized or successfully applied. Model context, affected elements and the resulting state must be checked separately.

The project explores how to preserve that separation when introducing language models into engineering workflows.

## 2. Verification-First Architecture

```text
Natural-language request
        ↓
Untrusted action proposal
        ↓
Deterministic validation and model-context checks
        ↓
Preview and explicit engineer approval
        ↓
Controlled Revit operation
        ↓
Model read-back verification and recorded outcome
```

AI interpretation, validation, approval, execution and verification are distinct stages. An accepted proposal is not permission to modify the model. A committed transaction alone is not a verified result.

## 3. Implemented Capabilities

**VERIFIED** means a recorded result within the stated test scope. **IMPLEMENTED BUT NOT VERIFIED** means code exists without sufficient evidence for the stated runtime scope. **PLANNED** means the capability is not complete.

| Capability | Evidence status and scope |
| --- | --- |
| Selected-window resizing, target-type creation and source-type preservation | **VERIFIED** in recorded native test scenarios. |
| Type-only creation without reassigning the selected window | **VERIFIED** in a recorded native scenario. |
| Straight-wall creation with approval and read-back checks | **VERIFIED** in recorded native scenarios. |
| Exact-result reuse to avoid duplicate operations | **VERIFIED** in selected native resize and wall scenarios. |
| Intent boundaries, failure handling and additional validation cases | **VERIFIED** within offline mock, pure-logic or simulated-API tests; not equivalent to native coverage. |
| Schematic planning and batch-approval previews | **VERIFIED** offline; this does not establish model creation. |
| DWG evidence, centerline preview and atomic batch execution | **IMPLEMENTED BUT NOT VERIFIED** for native end-to-end completion in the reviewed evidence set. Offline checks are available. |
| Connecting schematic plan approval to complete model execution | **PLANNED**; not a delivered execution capability. |

## 4. Recorded Test Evidence

Reviewed private records include:

- **Native execution audits:** eight completed window reassignment results and one type-only result in a versioned resize audit; six completed wall creations and two exact-existing-wall no-op results in a versioned wall audit. An earlier resize audit also records a verified no-op.
- **Offline evidence:** 22 recorded test-runner logs covering contracts, mocked providers, deterministic geometry, approval, simulated execution and UI integration. Some runners invoke others; their assertion counts must not be summed as unique tests.
- **UI evidence:** offline WPF renders and binding/handler checks. These are not screenshots proving live Revit behavior.

Native audits, simulated APIs and mocked inference are separate evidence categories. The records cover selected scenarios, not every model or family. Private audit records are not externally attested, and not every record identifies its exact executable build.

This documentation-only repository does not publish raw audits or test harnesses. These results are therefore reported engineering evidence, not independently reproducible public CI results.

## 5. Safety and Reliability Principles

- Treat language-model output as untrusted input.
- Reject unsupported or ambiguous proposals rather than inventing missing engineering information.
- Require explicit approval for the reviewed action before mutation.
- Preserve original model state where the operation requires it.
- Re-read model state instead of equating API completion with correctness.
- Use controlled recovery or manual review when an operation cannot be verified.

Read-back verification is performed within the application. It is not third-party certification or proof of structural, regulatory or construction correctness.

## 6. Current Limitations

- Native test coverage is limited; broader family, project and collaboration scenarios remain unverified.
- Recovery paths have offline simulation coverage; comprehensive native failure-injection and rollback validation has not been established.
- The Ollama-based inference path operates locally. Fully disconnected end-to-end operation has not yet been independently validated. A separate cloud-model integration path exists in the codebase.
- Minimum RAM/VRAM, required GPU and inference performance have not been established by a controlled benchmark.
- Revit 2027 compatibility has not been built or live-validated.
- The prototype is not autonomous building design, structural analysis or building-code compliance software.

## 7. Research Direction

Further work is **PLANNED**, not claimed as complete: broader native validation, independently reproducible evidence and evaluation of approved multi-action workflows. These directions do not imply additional released capabilities.

## 8. Repository Scope

This repository is intended for high-level architecture, carefully scoped technical claims and approved, sanitized demonstration material.

It is not a source-code distribution or an installation package. Proprietary implementation details, internal prompts, decision rules, raw model identifiers, private logs, test harness internals, binaries and personal configuration are excluded from the intended public scope.
