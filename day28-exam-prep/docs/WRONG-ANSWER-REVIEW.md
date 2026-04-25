# Structured Wrong-Answer Review

## Entry 1
- Question topic: `terraform state mv` behavior
- What I answered: It renames infrastructure in AWS.
- Correct answer: It moves resource address mapping inside Terraform state only.
- Why I was wrong: I mixed state operations with provider-side infrastructure actions.
- Doc reference: https://developer.hashicorp.com/terraform/cli/commands/state/mv
- Hands-on fix: Ran `terraform state mv` in a test project and verified no direct AWS object mutation occurred.

## Entry 2
- Question topic: `terraform apply -refresh-only`
- What I answered: It updates infrastructure to match configuration.
- Correct answer: It syncs state with real infrastructure without changing resources.
- Why I was wrong: I confused drift/state sync behavior with normal apply reconciliation.
- Doc reference: https://developer.hashicorp.com/terraform/cli/commands/apply
- Hands-on fix: Changed resource metadata manually, ran refresh-only apply, confirmed state alignment.

## Entry 3
- Question topic: Backend vs provider responsibilities
- What I answered: Provider controls state locking.
- Correct answer: Backend controls state storage/locking; provider controls API calls to infrastructure.
- Why I was wrong: I grouped backend/provider as one configuration concern instead of separate layers.
- Doc reference: https://developer.hashicorp.com/terraform/language/settings/backends/configuration
- Hands-on fix: Compared local backend behavior against remote backend behavior in concurrent command test.

## Entry 4
- Question topic: Sibling module communication
- What I answered: Sibling modules can directly reference each other's resources.
- Correct answer: Modules communicate through root-level input/output wiring.
- Why I was wrong: I ignored module boundaries and over-assumed shared scope.
- Doc reference: https://developer.hashicorp.com/terraform/language/modules/syntax
- Hands-on fix: Built a mini module lab and passed outputs from one module into another through root inputs.

## Entry 5
- Question topic: Terraform Cloud policy timing
- What I answered: Policies run after apply.
- Correct answer: Policies evaluate as gates after plan and before apply.
- Why I was wrong: I treated policy checks as audit-only instead of enforcement checkpoints.
- Doc reference: https://developer.hashicorp.com/terraform/cloud-docs/policy-enforcement
- Hands-on fix: Reviewed Terraform Cloud run stages and mapped policy checkpoint to the plan/apply boundary.

## Extra Entries (Condensed)
- `taint` modern usage: replaced by `apply -replace`.
- State lock assumptions: lock applies to operations that mutate state lifecycle.
- CLI scenario misses: subtle flags changed command scope more than expected.
