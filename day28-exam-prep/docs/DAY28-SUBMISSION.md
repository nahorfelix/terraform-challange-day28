# Day 28 — Exam Preparation: Practice Exams 1 & 2

## Exam Scores
- Exam 1: **47/57 (82%)**
- Exam 2: **51/57 (89%)**

My score improved by 7% in Exam 2. I attribute that to better pacing, less overthinking, and fast elimination of distractors.

## Domain Accuracy Table

| Domain | Attempted | Correct | Accuracy |
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

No domain fell below 70%. Lowest domains were CLI and Configuration.

## Wrong-Answer Analysis (5 entries)

1. **Topic:** `terraform state mv`
- My answer: Renames infra in AWS
- Correct: Moves resource address in Terraform state only
- Why wrong: Confused state mapping vs provider-side changes
- Doc: https://developer.hashicorp.com/terraform/cli/commands/state/mv
- Hands-on fix: Ran `terraform state mv` and confirmed no direct AWS change

2. **Topic:** `terraform apply -refresh-only`
- My answer: Updates infra to match config
- Correct: Updates state to match real infra, no infra mutation
- Why wrong: Mixed refresh-only with normal apply behavior
- Doc: https://developer.hashicorp.com/terraform/cli/commands/apply
- Hands-on fix: Changed value manually, ran refresh-only, verified state sync

3. **Topic:** Backend vs provider
- My answer: Provider controls locking
- Correct: Backend handles state/locking, provider handles resource API calls
- Why wrong: Blended two different responsibilities
- Doc: https://developer.hashicorp.com/terraform/language/settings/backends/configuration
- Hands-on fix: Compared local vs remote backend behavior in concurrent runs

4. **Topic:** Module communication
- My answer: Sibling modules can reference each other directly
- Correct: Data flows through root inputs/outputs
- Why wrong: Ignored module boundary rules
- Doc: https://developer.hashicorp.com/terraform/language/modules/syntax
- Hands-on fix: Built mini module chain using root-level output/input wiring

5. **Topic:** Terraform Cloud policy timing
- My answer: Policy runs after apply
- Correct: Policy gates apply after plan
- Why wrong: Treated policy as audit, not pre-apply control
- Doc: https://developer.hashicorp.com/terraform/cloud-docs/policy-enforcement
- Hands-on fix: Reviewed run stages and mapped policy checkpoint to plan/apply boundary

## Hands-On Revision

State drill:
```bash
terraform state list
terraform state show aws_s3_bucket.example
terraform state mv aws_s3_bucket.example aws_s3_bucket.example_moved
terraform state rm aws_s3_bucket.example_moved
```

CLI drill:
```bash
terraform plan -destroy
terraform apply -refresh-only
terraform apply -replace="aws_instance.example"
```

I also created a mini module lab to practice variables, outputs, and root wiring.

## Pattern Recognition
Most misses were not definition questions; they were behavior questions. The recurring mistake pattern was confusing:
- state vs infrastructure effects,
- command intent vs side effects,
- and workflow stage order (plan/policy/apply).

## Plan for Days 29–30
- **Day 29:** CLI edge cases, state command drills, module wiring drills.
- **Day 30:** Final timed mock, wrong-answer log review, final pass on CLI + Configuration.
