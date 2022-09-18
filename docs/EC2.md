# EC2 tasks

[`Return`](/README.md) to main

## Description

This role is used to manage keys and instances in the Elastic Compute Cloud (EC2) in Amazon Web Services (AWS).

- ### ```role_name```: [`create`](/ec2/create/)

  Create a new EC2 Instance or Key depending on the ```role_action``` specified.&nbsp;  The valid values for ```role_action``` are ```instance``` and ```key```.&nbsp; The values for ```wait``` and ```assign_public_ip``` are ```true``` or ```false``` (other Ansible accepted values also work).&nbsp; The only state allowed for ```ec2_instance_state``` or ```ec2_key_state``` for this role is ```present```.&nbsp; Specify ```tags``` as name a list of name/value pairs.

  &nbsp;

  > #### create variables when ```role_action``` == '```instance```'
  >
  >    | Description         | Variable name             | Required | Where specified       |
  >    | ------------------- | ------------------------- |:--------:| --------------------- |
  >    | Instance Name       | ```instance_name```       | yes      | extra_vars            |
  >    | SSH Key Name        | ```key_name```            | yes      | role vars, extra_vars |
  >    | Instance Type       | ```instance_type```       | yes      | role vars, extra_vars |
  >    | AMI Image           | ```image_name```          | no       | role vars, extra_vars |
  >    | Wait                | ```wait```                | yes      | role vars, extra_vars |
  >    | Tags                | ```instance_tags```       | yes      | role vars, extra_vars |
  >    | Number of Instances | ```count```               | yes      | extra_vars            |
  >    | Region              | ```region```              | yes      | role vars, extra_vars |
  >    | VPC Subnet Id       | ```vpc_subnet_id```       | yes      | role vars, extra_vars |
  >    | Assign Public IP    | ```assign_public_ip```    | yes      | role vars, extra_vars |
  >    | Instance State      | ```ec2_instance_state```  | yes      | role vars, extra_vars |
  &nbsp;

  > #### create variables when ```role_action``` == '```key```'
  >
  >    | Description         | Variable name                      | Required | Where specified       |
  >    | ------------------- | ---------------------------------- |:--------:| --------------------- |
  >    | SSH Key Name        | ```key_name```                     | yes      | extra_vars            |
  >    | Region              | ```region```                       | yes      | role vars, extra_vars |
  >    | Key Material        | ```key_material``` (rsa-ssh data)  | no       | extra_vars            |
  >    | Key State           | ```ec2_key_state```                | yes      | role vars, extra_vars |
  >  
  > When ```key_material``` is not specified, the task returns the and sets a fact containing the material of the new key.

  &nbsp;

- ### ```role_name```: [`delete`](/ec2/delete/)

  Delete an EC2 Instance or Key depending on the role_action.&nbsp;  The valid values for ```role_action``` are ```instance``` and ```key```.&nbsp; The only state allowed for ```ec2_instance_state``` or ```ec2_key_state``` for this role is ```absent```.

  &nbsp;

  > #### delete variables when ```role_action``` == '```instance```'
  >
  >    | Description         | Variable name              | Required | Where specified       |
  >    | ------------------- | -------------------------- |:--------:| --------------------- |
  >    | Instance Ids        | ```instance_ids```         | yes      | extra_vars            |
  >    | Region              | ```region```          | yes      | role vars, extra_vars |
  >    | Instance State      | ```ec2_instance_state```   | yes      | role vars, extra_vars |
  &nbsp;

  > #### delete variables when ```role_action``` == '```key```'
  >
  >    | Description         | Variable name              | Required | Where specified       |
  >    | ------------------- | -------------------------- |:--------:| --------------------- |
  >    | SSH Key Name        | ```key_name```             | yes      | extra_vars            |
  >    | Region              | ```region```          | yes      | role vars, extra_vars |
  >    | Key State           | ```ec2_key_state```        | yes      | role vars, extra_vars |
  >  

  &nbsp;

- ### ```role_name```: [`update`](/ec2/update/)

  Rename an existing EC2 Instance.

  &nbsp;

  > #### update variables
  >
  >    | Description         | Variable name         | Required | Where specified       |
  >    | ------------------- | --------------------- |:--------:| --------------------- |
  >    | Instance Id         | ```instance_id```     | yes      | extra_vars            |
  >    | Region              | ```region```          | yes      | role vars, extra_vars |
  >    | Instance Name       | ```instance_name```   | yes      | extra_vars            |

  &nbsp;

- ### ```role_name```: [`power`](/ec2/power/)

  Set the power state of an EC2 instance depending on the value provided for ```ec2_instance_state```.&nbsp; The valid instance states are ```restarted```, ```running```, and ```stopped```.

  &nbsp;

  > #### power state variables
  >
  >    | Description         | Variable name              | Required | Where specified       |
  >    | ------------------- | -------------------------- |:--------:| --------------------- |
  >    | Instance Ids        | ```instance_ids```         | yes      | extra_vars            |
  >    | Region              | ```region```          | yes      | role vars, extra_vars |
  >    | Instance State      | ```ec2_instance_state```   | yes      | extra_vars            |

  &nbsp;

[`Return`](/README.md) to main
