# Hands-On Revision Plan

## State Management Drill
Commands executed:
```bash
terraform state list
terraform state show aws_s3_bucket.example
terraform state mv aws_s3_bucket.example aws_s3_bucket.example_moved
terraform state rm aws_s3_bucket.example_moved
```

Observed outcomes:
- `state list` confirmed tracked objects.
- `state show` exposed full tracked attributes.
- `state mv` changed address in state without mutating cloud resources.
- `state rm` removed resource from state only (resource still existed until separately destroyed/imported).

## CLI Behavior Drill
Commands executed:
```bash
terraform plan -destroy
terraform apply -refresh-only
terraform apply -replace="aws_instance.example"
```

Observed outcomes:
- `plan -destroy` generated full destroy plan safely before execution.
- `apply -refresh-only` updated state from current infrastructure conditions.
- `apply -replace` forced targeted recreation without blanket rebuild.

## Module Drill
- Built mini module in `../hands-on/module-lab/`.
- Called module from root with variable inputs and output references.
- Practiced passing output from one module into another root-level consumer.

## Completion Log
- [x] State drill completed
- [x] CLI behavior drill completed
- [x] Module drill completed
- [x] Wrong-answer remediation notes completed
