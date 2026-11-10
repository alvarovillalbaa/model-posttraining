# Model post-training specification

Last updated: 2026-11-10

Status: planned. No trainer, adapter, checkpoint importer, or package exists yet.

## Target consumer and interface

A user supplies a permitted existing checkpoint from any compatible source,
not a required checkout of model-pretraining.

- An adaptation request names the base weights/config/tokenizer artifact
  identities and hashes; the selected compatible adapter; method and seed;
  frozen training/validation inputs; explicit template and loss-mask policy;
  output/checkpoint destinations; and execution/resource limits.
- SFT consumes instruction/chat examples. Preference optimization consumes
  chosen/rejected records with their source identities. Reward-based adaptation
  consumes an explicit reward/environment contract and observed rollout data.
- Resume binds the base model, adaptation method, input identities, tokenizer,
  template and training state. Incompatible requests must fail visibly.
- Results include adaptation metrics/status, parent-model lineage, resumable
  state, and a portable adapted model or adapter with its configuration/hash.
  A consumer must know whether an adapter still requires base weights.

These are target behavioral interfaces, not implemented API signatures or a
released artifact schema.

## Prerequisites and boundaries

The first implementation selects one compatible local base model/format, an
authorized tiny SFT dataset, a fixed chat template, and a bounded runtime.
Model/data/teacher licensing and provider budget/access gates remain explicit.
No model or dataset is downloaded by reading this specification.

Model-pretraining owns base training. Model-distillation owns synthetic task/
response eligibility and preference construction. Open Evals owns reusable
evaluation definitions/results; this trainer invokes or consumes them rather
than creating a new evaluator service. RL environments own reusable task
dynamics. Serving and inference benchmark methodology belong to their own tools.

## Acceptance

The first SFT path must work in its own environment with an externally supplied
base artifact, preserve parent/data/code identities, apply the declared loss
mask, resume, and export a reloadable adapted artifact. Use a held-out split
separate from training. Later preference/RL methods need method-specific
behavior checks, explicit reward provenance, and regression evidence.

A local fixture or improving training loss is not proof of model quality,
safety, live provider acceptance, or research improvement.

[Blueprint](blueprint.md) · [Backlog](backlog.md) ·
[Source history](../sources/README.md)
