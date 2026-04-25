# Day 28 — Exam Preparation: Practice Exams 1 & 2

## Exam Scores
- Exam 1 score: **47/57 (82%)**
- Exam 2 score: **51/57 (89%)**

My Exam 2 score improved by 7%. I think the improvement came from better pacing, quicker elimination of distractors, and stronger recall after reviewing weak areas from Exam 1.

## Domain Accuracy Table

| Domain | Questions Attempted | Correct | Accuracy |
|---|---:|---:|---:|
| IaC concepts | 6 | 5 | 83% |
| Terraform's purpose | 8 | 8 | 100% |
| Terraform basics | 10 | 8 | 80% |
| Terraform CLI | 12 | 9 | 75% |
| Terraform modules | 6 | 5 | 83% |
| Core workflow | 4 | 4 | 100% |
| State management | 5 | 4 | 80% |
| Configuration | 4 | 3 | 75% |
| Terraform Cloud | 2 | 2 | 100% |

All domains remained above 70%. The most difficult areas were Terraform CLI and Configuration because questions tested exact command behavior and edge-case interpretation.

## Wrong-Answer Analysis

### Wrong Answer 1
- Question topic: `terraform state mv` behavior
- What I answered: It renames infrastructure in AWS
- Correct answer: It moves an object address in Terraform state only
- Why I was wrong: I mixed state address movement with provider-side infrastructure changes.
- Doc reference: https://developer.hashicorp.com/terraform/cli/commands/state/mv
- Hands-on fix: I moved a test resource with `terraform state mv` and verified no change occurred in AWS resources.

### Wrong Answer 2
- Question topic: `terraform apply -refresh-only`
- What I answered: It updates infrastructure to match configuration
- Correct answer: It updates state to reflect real infrastructure without changing resources
- Why I was wrong: I confused state refresh behavior with normal apply reconciliation.
- Doc reference: https://developer.hashicorp.com/terraform/cli/commands/apply
- Hands-on fix: I changed a value manually in console, ran `terraform apply -refresh-only`, and observed state sync.

### Wrong Answer 3
- Question topic: Backend vs provider responsibility
- What I answered: Provider controls state locking
- Correct answer: Backend controls state storage/locking; provider controls API interactions with infrastructure
- Why I was wrong: I grouped backend and provider under one concept and missed their distinct responsibilities.
- Doc reference: https://developer.hashicorp.com/terraform/language/settings/backends/configuration
- Hands-on fix: I compared local backend and remote backend behavior and observed locking behavior during concurrent commands.

### Wrong Answer 4
- Question topic: Module data flow
- What I answered: Sibling modules can directly reference each other’s resources
- Correct answer: Sibling modules communicate via root module inputs/outputs
- Why I was wrong: I overlooked module encapsulation boundaries and proper wiring through root module.
- Doc reference: https://developer.hashicorp.com/terraform/language/modules/syntax
- Hands-on fix: I built a mini module lab and passed output from one module into another through root inputs.

### Wrong Answer 5
- Question topic: Terraform Cloud policy enforcement timing
- What I answered: Policies run after apply
- Correct answer: Policies gate apply after plan
- Why I was wrong: I treated policy checks as audits rather than pre-apply controls.
- Doc reference: https://developer.hashicorp.com/terraform/cloud-docs/policy-enforcement
- Hands-on fix: I reviewed the Terraform Cloud run pipeline and mapped policy checkpoints to plan/apply stages.

## Hands-On Revision

### State management practice
I practiced core state commands against test resources:

```bash
terraform state list
terraform state show aws_s3_bucket.example
terraform state mv aws_s3_bucket.example aws_s3_bucket.example_moved
terraform state rm aws_s3_bucket.example_moved
```

Result: I confirmed state operations change Terraform tracking and do not directly change live infrastructure unless followed by apply actions.

### CLI behavior practice

```bash
terraform plan -destroy
terraform apply -refresh-only
terraform apply -replace="aws_instance.example"
```

Result: I reinforced differences between destroy planning, state refresh-only operations, and forced replacement behavior.

### Module workflow practice
I created a mini reusable module and consumed it from a root module to reinforce variable passing, outputs, and module boundaries.

## Pattern Recognition
After two exams, my most consistent misses were command-behavior nuance questions, especially those that distinguish:
- state changes vs infrastructure changes,
- workflow stage timing (plan/policy/apply),
- and module encapsulation vs direct references.

The key improvement need is precision in command semantics, not basic terminology.

## Plan for Days 29 and 30

### Day 29 focus
1. Terraform CLI edge cases (`-refresh-only`, `-replace`, `plan -destroy`)
2. State workflow drills (`state mv`, `state rm`, import/reconciliation)
3. Module wiring drills with output/input chaining

### Day 30 focus
1. Final timed mock exam under strict conditions
2. Rapid review of wrong-answer log only
3. Last revision pass on lowest domains (CLI and Configuration)
4. Exam-day strategy: pace control, flag-and-return method, elimination discipline
