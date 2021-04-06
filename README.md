# scalable-jenkins-ansible

Should create an EKS fargate Cluster with a running Jenkins Instance.

Based on this article: https://aws.amazon.com/de/blogs/containers/how-to-build-container-images-with-amazon-eks-on-fargate/

## AWS Ansible Collection Doku

There are two collections.

* Amazon AWS Collection, maintained by the Ansible cloud team: https://github.com/ansible-collections/amazon.aws
* Community AWS Collection, supported by the Ansible community: https://github.com/ansible-collections/community.aws

## Installating AWS Collection

    ansible-galaxy collection install -r requirements.yml

