# Post-training implementation blueprint

Last updated: 2026-11-10

Status: planned. Derived from original Lab section 12; the exact mixed source
is preserved in model-pretraining's pre-expansion history and identified in
[the relocation map](../sources/repository-expansion-map.json).

## SFT first

Start with a compatible external base checkpoint and a fixed chat template.
Mask the intended user/system tokens from training loss. Keep validation
separated by source, avoid benchmark-answer contamination, and bind evaluated
checkpoints to the exact training inputs and method.

## Preference optimization

Add one declared chosen/rejected objective after the SFT path works. Preserve
the source of preference labels and the parent checkpoint. DPO, IPO, KTO and
ORPO are method candidates inside this product, not separate repository owners
created by this split.

## Reward-based adaptation

Add a bounded reward/rollout interface only after the simpler adaptation path.
The original design names verifiable math, code, tool, structured-output and
citation tasks. An environment or evaluator supplies task truth; this product
owns the model update. Record reward versions and rollout identities.

SFT, preference, and reward-based runs remain separate controlled stages. A
candidate may be evaluated by Open Evals and coordinated by a research
controller; the trainer does not own automatic release promotion.

## Safety and portable output

Bind each adapted model to its base model, tokenizer, template, data, code,
method and environment. Preserve safety-data provenance and external regression
results. Export a complete model or an explicitly base-dependent adapter.
Deployment moderation and endpoint lifecycle are serving concerns.
