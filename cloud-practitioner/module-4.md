# MODULE 4
*Objectives*
- Describe the basic concepts of networking
- Describe the difference between public and private networking resources
- Explain a virtual private gateway using a real life scenario
- Explain a virtual private network (VPN) using a real life scenario
- Describe the benefit of AWS Direct Connect
- Describe the benefit of hybrid deployments
- Describe the layers of security used in an IT strategy
- Describe the services customers use to interact with the AWS global network

## Connectivity to AWS
*Internet Gateway*: allows public traffic fromt he internet to access your VPC

*Virtual Priavate Gateway*: allows you to access private resources in a VPC

*Virtual Private Cloud* or *VPC* is why AWS works at all. VPC allows AWS customers to secure their resources in AWS, just like they would on premises using networking principles like subnets and and routing.

AWS *Direct Connect* allos you to establish a dedicated private connection between your data center and a VPC.

## Subnets and Network ACLs
Subnets allow us to group resources together and keep them separate. This is useful because it helps us reason about our network and keep it organized.

It's also useful because you can make a subnet private or public, which means we can mark of portions of our network as inaccessible to anyone not on the private side of the gateway. This gives us better control over how clients interact with our system.

*Network access control lists* or *ACL*s are virtual firewalls that control inbound and outbound trafic at the subnet level. They work like passport control officers in airports. "If a traveler is on an approved list, they are able to get through. However, if they are not on the approved list or are explicitly on a list of banned travelers, they cannot."

By default our account's ACL allows all inbound and outbound traffic, but we can modify it by adding our own rules. For custom ACLs, all inbound and outbound traffic is denied until you add rules to specify which traffic to allow. We can also deny any packet that doesn't match any of the rules in the ruleset.

### Stateless packet filtering
ACLs perform _stateless_ packet filtering. They remember nothing and check all packets inbound and outbound.

## Security groups
A *security group* is a virtual firewall that operates on the instance level. By default a security group denies all inbound traffic and allows all outbound traffic. Security groups can be shared across multiple instances, but the packet filtering happens at each individual instance.

### Stateful packet filtering
Security groups perform _stateful_ packet filtering. They remember previous decisions made for incoming packets.

## Conclusion
*ACL*s work on the subnet level and are _stateless_ -- they check every packet regardless of direction.

*Security groups* operate on the instance level and are _stateful_ -- they remember decisions made in the past and doesn't check rules if it recognizes the packet from an earlier transaction.

