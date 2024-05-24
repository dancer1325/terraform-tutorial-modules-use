# Learn Terraform Modules Create
This repo is a companion repo to the [Use Modules from the Registry tutorial](https://developer.hashicorp.com/terraform/tutorials/modules/module-use)

## Goal
* Provisions
  * VPC + subnets + internet gateway + NAT gateway
  * EC2 instances
* Use the modules
  * [vpc](https://registry.terraform.io/modules/terraform-aws-modules/vpc/aws/latest) &
    * [variables](https://github.com/terraform-aws-modules/terraform-aws-vpc/blob/master/variables.tf)
    * [inputs](https://github.com/terraform-aws-modules/terraform-aws-vpc?tab=readme-ov-file#inputs)
  * [ec2-instance](https://registry.terraform.io/modules/terraform-aws-modules/ec2-instance/aws/latest)
    * [inputs](https://github.com/terraform-aws-modules/terraform-aws-vpc?tab=readme-ov-file#inputs)

* TODO:

## How to run?
* `terraform init`
* `terraform apply`
  * Problems:
    * Problem1: No output got
      * Solution: Update aws.version & `terraform init -upgrade`
    * Problem2: Unsupported arguments 'enable_classiclink', 'enable_classiclink_dns_support'
      * Solution: Update modules.vpc & modules.ec2 versions
* `terraform destroy`

## Notes:
* 'variables.tf'
  * == module arguments / could change
* 'outputs.tf'
  * `module.moduleName.outputName`
    * way to refer to output values
* '.terraform.modules/*'
  * modules installed once you run `terraform init` OR `terraform get`
  * if you use local modules -> symlinks are created