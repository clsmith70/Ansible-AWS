# EC2 tasks

[`Return`](/README.md) to main

## Description

This role is used to manage keys and instances in the Elastic Compute Cloud (EC2) in Amazon Web Services (AWS).

- ### ```role_name```: [`create`](/ec2/create/)

  Create a new EC2 Instance or Key depending on the ```role_action``` specified.&nbsp;  The valid values for ```role_action``` are ```instance``` and ```key```.

  &nbsp;

  > #### variables when ```role_action``` == '```instance```'
  >
  >    | Description         | Variable name                      | Required | Where specified       |
  >    | ------------------- | ---------------------------------- |:--------:| --------------------- |
  >    | SSH Key Name        | ```key_name```                     | yes      | role vars, extra_vars |
  >    | Instance Type       | ```instance_type```                | yes      | role vars, extra_vars |
  >    | AMI Image           | ```image_name```                   | no       | role vars, extra_vars |
  >    | Wait                | ```wait``` (yes/no)                | yes      | role vars, extra_vars |
  >    | Instance Group      | ```instance_group```               | yes      | extra_vars            |
  >    | Number of Instances | ```count```                        | yes      | extra_vars            |
  >    | Region              | ```region```                       | yes      | role vars, extra_vars |
  >    | VPC Subnet Id       | ```vpc_subnet_id```                | yes      | role vars, extra_vars |
  >    | Assign Public IP    | ```assign_public_ip``` (yes/no)    | yes      | role vars, extra_vars |
  >    | Instance State      | ```ec2_instance_state``` (present) | yes      | role vars, extra_vars |
  &nbsp;

  > #### variables when ```role_action``` == '```key```'
  >
  >    | Description         | Variable name                      | Required | Where specified       |
  >    | ------------------- | ---------------------------------- |:--------:| --------------------- |
  >    | SSH Key Name        | ```key_name```                     | yes      | extra_vars            |
  >    | Region              | ```region```                       | yes      | extra_vars            |
  >    | Key Material        | ```key_material``` (rsa-ssh data)  | no       | role vars             |
  >    | Key State           | ```ec2_key_state``` (present)      | yes      | role vars, extra_vars |
  >  
  > When ```key_material``` is not specified, the task returns the material of the new key and sets a fact containing the material of the new key.
  &nbsp;

- ### ```role_name```: [`delete`](/ec2/delete/)

- ### ```role_name```: [`power`](/ec2/power/)

[`Return`](/README.md) to main
