# 🔹 VPC Block #
Your VPC uses 10.0.0.0/16, giving:

2^(32−16) = 65,536 total IPs
This is the full address space all subnets come from.

# 🔹 /24 Subnets #
Each subnet is /24, meaning:

2^(32-24) = 256 total IPs
* AWS reserves 5, leaving 251 usable. *

Example: 10.0.1.0/24  
Usable range: 10.0.1.1 → 10.0.1.254

# 🔹 Subnet Increments #
A /24 has a block size of 256, so each new subnet increases the third octet by 1:

10.0.1.0

10.0.2.0

10.0.3.0

10.0.4.0

# 🔹 Quick CIDR Block Sizes #
/24 → 256 IPs

/25 → 128 IPs

/26 → 64 IPs

/27 → 32 IPs