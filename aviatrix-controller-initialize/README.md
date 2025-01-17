## Aviatrix - Terraform Modules - Aviatrix Controller Initialize

### Description

This Terraform module initializes a newly created Aviatrix Controller.

### Usage

``` terraform
module "aviatrix_controller_init" {
  source              = "github.com/AviatrixSystems/terraform-modules.git//aviatrix-controller-initialize?ref=master"
  admin_email         = "<<< enter the administrator email address >>>"
  admin_password      = "<<< enter the new administrator password >>>"
  private_ip          = "<<< enter the Aviatrix Controller's private IP address (initial admin password) >>>"
  public_ip           = "<<< enter the Aviatrix Controller's public IP address >>>"
  access_account_name = "<<< enter the account name mapping to your AWS account in the Aviatrix Controller >>>"
  aws_account_id      = "<<< enter the aws account id >>>"
  vpc_id              = "<<< insert VPC here, ie. vpc-xxxxxx >>>"
  subnet_id           = "<<< insert public subnet id, ie.: subnet-9x3237xx >>>"
  customer_license_id = "<<< enter the customer license id (optional) >>>" 
}


output "lambda_result" {
  value = "${module.aviatrix_controller_init.result}"
}
```

### Variables

- **admin_email**

  The administrator's email address. This email address will be used for password recovery as well as for notifications
  from the Controller.

- **admin_password**

  The administrator's password. The default password is the Controller's private IP addresses. It will be changed to this
  value as part of the initialization.

- **private_ip**

  The Controller's private IP address.

- **public_ip**

  The Controller's public IP address.

- **access_account_name**

  A friendly name mapping to your AWS account ID.

- **aws_account_id**

  The AWS account ID.
  
- **vpc_id**

  The ID of the VPC where the Controller is launched.

- **name_prefix**

  A prefix to be added to the aviatrix lambda policy. Default value is "".

- **tags** 

  Additional map of tags passed to mark resources create by module. Default value is {}.

- **subnet_id**

  The ID of the subnet where the Controller instance resides.

- **customer_license_id**

  The customer license ID, optional. Required if using a BYOL controller.
  
- **controller_version**
  
  The version to which you want initialize the Aviatrix controller.
    
- **controller_launch_wait_time**
 
  Time in second to wait for controller to be up. Default value is 210.

- **ec2_role_name**

  EC2 role name. Default value is "aviatrix-role-ec2".

- **app_role_name**

  APP role name. Default value is "aviatrix-role-app".

### Outputs

- **result**

  The status of lambda execution.
