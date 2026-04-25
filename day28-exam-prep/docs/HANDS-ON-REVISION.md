# Hands-On Revision Plan

Complete practical drills for every domain below 70%.

## State Management Drill
```bash
terraform init
terraform state list
terraform state show <resource>
terraform state mv <old_addr> <new_addr>
terraform state rm <resource>
```

## Modules Drill
- Create a mini module in `../hands-on/module-lab/`
- Call it from a root config
- Pass variables and consume outputs

## CLI/Core Workflow Drill
```bash
terraform fmt -recursive
terraform validate
terraform plan
terraform apply -auto-approve
terraform destroy -auto-approve
```

## Terraform Cloud Drill (if weak)
- Create workspace
- Configure variables
- Trigger run
- Review plan/apply output

## Completion Log
- [ ] State drill completed
- [ ] Module drill completed
- [ ] Core workflow drill completed
- [ ] Terraform Cloud drill completed (if applicable)
