# terraform.

* for deploying application we need infrastructure
* by using this terraform we can create infrastucture
* Infrastructure as Code (IaC)
* This means expressing our infra needs in the form of some template.
* While creating/realizing the infra, pass the dynamic values. 
* IaC which runs on any virtual platform.
* we have to do
  * Define our infrastructure as a template in Terraform   
  * Execute the template to create infrastructure.
* we need to write these templates in Hashicorp Configuration Language (HCL)
* Here we express what we want in the template which is referred as Desired State
* Now when execute terraform will try to create infra to match your Desired State.
* 
* ### Idempotence: 
  * This is property which states that executing once or multiple times will have the same result

* ## Provider: 
* Provider: Provider tells terraform where do you want to create the infra, Generally there will be   authentication details as well.
**ex** 
```
provider "aws" {
  region     = "us-west-2"
  access_key = "my-access-key"
  secret_key = "my-secret-key"
}
```


