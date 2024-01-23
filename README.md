# WebsiteForRoute53
Template that creates websites with different content in different VPCs

- We'll totally create "4 Linux" instances and "1 Windows" instance.
   
1. Create EC2 in default VPC as named  "N.virginia_1"
```bash
Region: "N.Virginia"
VPC: Default VPC
Subnet: PublicA
Sec Group: "Route 53 Sec"
```
- user data: 

```bash
#!/bin/bash

dnf update -y
dnf install -y httpd
dnf install -y wget
cd /var/www/html
wget https://raw.githubusercontent.com/awsdevopsteam/route-53/master/N.virginia_1/index.html
wget https://raw.githubusercontent.com/awsdevopsteam/route-53/master/N.virginia_1/N.virginia_1.jpg
systemctl start httpd
systemctl enable httpd

```

2. Create EC2 in default VPC as named "Geo-Asia"

```bash
Region: "N.Virginia"
VPC: Default VPC
Subnet: PublicA
Sec Group: "Route 53 Sec"
```

- user data:

```bash
#!/bin/bash

dnf update -y
dnf install -y httpd
dnf install -y wget
cd /var/www/html
wget https://raw.githubusercontent.com/awsdevopsteam/route-53/master/geo-japon/index.html
wget https://raw.githubusercontent.com/awsdevopsteam/route-53/master/geo-japon/Tsubasa.jpg
systemctl start httpd
systemctl enable httpd

```

3. Create EC2 in default VPC as named "Geo-Europe"
```bash
Region: "N.Virginia"
VPC: Default VPC
Subnet: PublicA
Sec Group: "Route 53 Sec"
```
- user data:

```bash
#!/bin/bash

dnf update -y
dnf install -y httpd
dnf install -y wget
cd /var/www/html
wget https://raw.githubusercontent.com/awsdevopsteam/route-53/master/frankfurt/index.html
wget https://raw.githubusercontent.com/awsdevopsteam/route-53/master/frankfurt/frankfurt.jpg
systemctl start httpd
systemctl enable httpd
```

4. Create EC2 in VPC of  "clarus-vpc-a" named "Local"

```bash 
Region: "N.Virginia"
VPC: 'clarus-vpc-a'-public 
Subnet: PublicA
Sec Group: ssh-http---->0.0.0.0/0

```

- user data:

```bash
#!/bin/bash

dnf update -y
dnf install -y httpd
dnf install -y wget
chkconfig httpd on
cd /var/www/html
wget https://raw.githubusercontent.com/awsdevopsteam/route-53/master/local/index.html
wget https://raw.githubusercontent.com/awsdevopsteam/route-53/master/local/Local.jpg
service httpd start

```
5. Create "Windows" instance in VPC of  "clarus-vpc-a" named "Windows"

```bash 
Region: "N.Virginia"
VPC: 'clarus-vpc-a'-public
Subnet: PublicA
Sec Group: RDP---->0.0.0.0/0
