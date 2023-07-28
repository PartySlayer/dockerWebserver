# dockerWebserver

Phase 1 of the Infrastructure Automation project

The core skill trained in this phase is AWS networking.
This phase is about launching an EC2 instance in a VPC.

The core skill trained is AWS networking.

I started creating a new VPC on AWS, using IPv4 CIDR 10.1.0.0/16.
![VPC](https://github.com/PartySlayer/dockerWebserver/assets/120326157/d2d06284-4a28-464e-bd0c-7abbcfa1def4)

Within this VPC, i then proceeded to create 2 subnets.
![subnet](https://github.com/PartySlayer/dockerWebserver/assets/120326157/58c98c38-d7ca-4640-9d44-bc2d7d6b0340)

I made sure that CIDR ranges wouldn't overlap, then set the subnets to automatically set a public IPv4 to every instance launched into them.
![subnet1](https://github.com/PartySlayer/dockerWebserver/assets/120326157/6cc36a3a-c89b-4835-aff9-0296b7031dac)

In order for the resources to connect to the internet, I had to create an Internet Gateway and attach it to the VPC.
![iG2](https://github.com/PartySlayer/dockerWebserver/assets/120326157/baab88b5-9a97-4548-9d9e-5f06aa613435)

This would carry out NAT AND provide a target in the route table.

I infact edited the ruotes so that all public traffic would be directed to the internet gateway, then associated the previosuly created subnets to this routing table.
![routes](https://github.com/PartySlayer/dockerWebserver/assets/120326157/07bfa50d-836a-4610-9a8f-7d2fa8af36c8)

The last thing to setup was the security group, which acts as a virtual firewall.
![sG](https://github.com/PartySlayer/dockerWebserver/assets/120326157/8d65a103-a2f7-485c-9166-fbe350623d4f)

It would filter inbound traffic.
![sG1](https://github.com/PartySlayer/dockerWebserver/assets/120326157/7c2fcc77-848c-4f58-80bd-c1e25b25b10b)

Finally I could start launching an EC2 istance.
I picked RHEL9 for the AMI.
![launch](https://github.com/PartySlayer/dockerWebserver/assets/120326157/b45c5a83-7a2d-4302-9114-3d7f65138081)

Once network and storage configuration were set, I had to create a new key pair.
![launch1](https://github.com/PartySlayer/dockerWebserver/assets/120326157/cf306d3a-fcca-4b65-b36a-cd6f373c393c)

The server was up and running at this point.
![launch2](https://github.com/PartySlayer/dockerWebserver/assets/120326157/d6da4c8f-029d-43b4-8b42-6d4072cb28c3)

After copying the private key on my VM I changed the .pem file permissions so that user/owner could only read and group and other could do nothing.
Finally, the server was reachable via ssh.
![launch3](https://github.com/PartySlayer/dockerWebserver/assets/120326157/62b4fcb4-cafc-4dd4-a63f-a71a21d556b2)


