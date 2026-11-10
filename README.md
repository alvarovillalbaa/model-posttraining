# model-posttraining

Last updated: 2026-11-10

Adapt an existing language-model checkpoint with supervised, preference, or reward-based post-training.

**Status: planned.** This repository contains the product boundary, target
interfaces, inherited requirements, and a scoped implementation backlog. It has
no executable engine or installable package.

## Independent consumer

A user with a compatible, permitted base checkpoint can adapt it without first using model-pretraining. The tool consumes explicit model, tokenizer, data/reward, and run configuration inputs and exports an adapted model or adapter.

## Start here

Read [the specification](docs/specs/README.md),
[implementation blueprint](docs/specs/blueprint.md), and
[scoped backlog](docs/specs/backlog.md). The specification is usable without a
runtime installation; implementation acceptance is still future work.

## Ownership

This component owns SFT chat formatting/loss masking, preference objectives,
reward-based model adaptation, adaptation checkpoint/resume, and portable
adapted-model or adapter export.

The first independent consumer supplies an existing base model. Optional base
models from [model-pretraining](https://github.com/alvarovillalbaa/model-pretraining)
use the same artifact seam. Synthetic/preference data construction remains in
model-distillation; generic scoring remains in open-evals; reusable environment
dynamics remain in rl-environments.

## Composition and terms

Lab may assemble pinned releases of this component; this component never
requires Lab or a sibling checkout. Exchanges use explicit versioned artifact
or endpoint references. Optional adapters must declare their own dependencies.

[Source history and relocation map](docs/sources/README.md) explains the split.
MIT covers authored code and documentation. Third-party models, data, tools,
and services retain their own terms. No source recovery, paid job, provider
acceptance, or scientific result is established by these specifications.
