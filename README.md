# scalable-jenkins-ansible

Should create an EKS fargate Cluster with a running Jenkins Instance.

Based on this article: https://aws.amazon.com/de/blogs/containers/how-to-build-container-images-with-amazon-eks-on-fargate/

## AWS Ansible Collection Doku


https://github.com/ansible-collections/community.aws/blob/main/docs/community.aws.aws_eks_cluster_module.rst

## Installating AWS Collection

    ansible-galaxy collection install -r requirements.yml



    - name: Getting VPC ID
      ansible.builtin.shell: >
        aws eks describe-cluster --name {{ eks_cluster_name }} \
        --region {{ eks_region }} \
        --query "cluster.resourcesVpcConfig.vpcId" \
        --output text
      register: vpc_id_fact
      
    - set_fact:
        vpc_id: "{{ vpc_id_fact.stdout }}"

    - name: VPC ID
      debug: 
        msg: "vpc id: {{ vpc_id }}"

    - name: List supported AWS endpoint services
      amazon.aws.ec2_vpc_net_info:
        vpc_ids: "{{ vpc_id }}"
      register: vpn_conn_info

    - name: Debug supported_endpoint_services
      debug:
        msg: "msg: {{ vpn_conn_info }}"