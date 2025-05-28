eks etcd is stored in ebs, so you can configure your etcd from there.
And if oyu want to provide encryption to it, you can do it using aws kms.


Enabling secret encryption with a new AWS Key Management Service (KMS) key in an existing Amazon Elastic Kubernetes Service (EKS) cluster is critical to securing sensitive data stored in the cluster’s etcd key-value store. Amazon EKS is a service for running and managing containerized applications, storing configuration data and secrets, etc., and is a distributed data store. By default, these secrets are not encrypted, posing potential security risks. Integrating AWS KMS with Amazon EKS allows for the encryption of these secrets, leveraging AWS KMS’s capabilities to manage cryptographic keys and control their use across AWS services and applications.

![](https://media.tutorialsdojo.com/public/Amazon-EKS-27072023.jpg)

The process involves creating an AWS KMS key specifically for the EKS cluster and configuring the cluster to encrypt secrets before they are saved in etcd. This setup ensures that all sensitive information within the etcd database is encrypted at rest, enhancing data security. By adopting this approach, organizations can significantly improve their security posture, ensuring that sensitive data and credentials are protected according to industry standards and compliance requirements, thus maintaining data confidentiality and integrity within their Kubernetes environments.

Hence, the correct answer is: **Enable secret encryption with a new AWS KMS key on an existing Amazon EKS cluster to encrypt sensitive data stored in the EKS cluster’s etcd key-value store.**

The option that says: **Use AWS Secrets Manager with a new AWS KMS key to securely manage and store sensitive data within the EKS cluster’s etcd key-value store** is incorrect. AWS Secrets Manager is a powerful tool for managing secrets but it doesn’t directly address encrypting data within the etcd key-value store of an EKS cluster. Secrets Manager is more about managing and retrieving secrets rather than encrypting data within etcd.

The option that says: **Enable default Amazon EBS volume encryption for the account with a new AWS KMS key to ensure encryption of sensitive data within the Amazon EKS cluster** is incorrect. Enabling default Amazon EBS volume encryption is a way to ensure that data at rest in EBS volumes is encrypted. However, the EBS volumes are primarily used for persistent storage of the worker nodes. They are not directly related to the storage of sensitive configuration data and credentials within the EKS cluster’s etcd key-value store.

The option that says: **Use Amazon EKS default options and the Amazon Elastic Block Store (Amazon EBS) Container Storage Interface (CSI) driver as an add-on to securely store sensitive data within the Amazon EKS cluster** is incorrect. Amazon EBS CSI driver enables Amazon Elastic Block Store (EBS) volumes as persistent storage for Kubernetes applications running on the Amazon EKS. While this can provide secure persistent storage for your microservices, it does not address the specific requirement of securely storing sensitive data within the EKS cluster’s etcd key-value store.

