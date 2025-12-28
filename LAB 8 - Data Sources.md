## Data sources

```
cd ~
```
```
mkdir lab8 && cd lab8
```
```
vi data.tf
```

Add the given lines, by pressing "INSERT" 
```
provider "aws" {
  region = "ap-south-1"
}

data "aws_ami" "ubuntu" {
  most_recent = true
  owners      = ["099720109477"]

  filter {
    name   = "name"
    values = ["ubuntu/images/hvm-ssd/ubuntu-jammy-22.04-amd64-server-*"]
  }

  filter {
    name   = "virtualization-type"
    values = ["hvm"]
  }
}

resource "aws_instance" "ubuntu_server" {
  ami           = data.aws_ami.ubuntu.id
  instance_type = "t3.micro"

  tags = {
    Name = "Ubuntu-T3-Micro"
  }
}

```

Save the file using "ESCAPE + :wq!"

```
terraform init
```
```
terraform plan
```
```
terraform apply
```
```
terraform destroy
```
```
cd ~
rm -rf lab8
```
