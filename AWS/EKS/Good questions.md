A retail company is migrating its supply chain application to Amazon Elastic Kubernetes Service (Amazon EKS). The company requires pods in the EKS cluster to use custom subnets in its existing VPC. Additionally, the pods must securely communicate with other resources within the VPC, while adhering to compliance requirements.

Which solution will meet these requirements?



**Use the Amazon VPC CNI plugin for Kubernetes. Configure the custom subnets in the VPC and associate the subnets with the EKS cluster to allow pods to use them:** This is correct because the Amazon VPC CNI plugin allows EKS pods to receive IP addresses from the specified custom subnets within the VPC. This ensures that the pods can securely communicate with other resources in the VPC.

**Set up AWS Transit Gateway to manage the routing between custom subnets and the EKS pods for secure communication within the VPC:** This is incorrect because AWS Transit Gateway is primarily used for connecting multiple VPCs or on-premises networks. It is not needed for pod-level subnet configuration within a single VPC.

**Configure an AWS Site-to-Site VPN between the custom subnets and the EKS cluster to enable secure communication for the pods:** This is incorrect because the VPC and EKS cluster are already within the same AWS environment, and a VPN is unnecessary for communication within the same VPC.

**Define Kubernetes network policies that enforce pod placement on specific nodes residing in the custom subnets within the VPC:** This is incorrect because Kubernetes network policies are used to control traffic flow between pods, not to configure subnet usage for pods.



