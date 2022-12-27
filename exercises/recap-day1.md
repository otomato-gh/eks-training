Your machine is preinstalled with:

 - aws cli

- eksctl

- kubectl 1.23



--



Pre-requisite:  Generate an ssh keypair by running: 

`ssh-keygen` with default inputs.



--



Please create a new EKS cluster by:



1. Generating a cluster.yaml file by running: `eksctl create cluster --name training-fg --region eu-west-1 --dry-run > cluster.yaml`

2. Edit cluster.yaml so that:

  a.  your managed node group is called "ng-1"

  b. Set instance `volumeSize` to 20 Gb

  c. Set managed nodegroup desired, min size to 2 instances. Set max size to 5 instances.

  d. Set the following `withAddonPolicies` to `true`:  `externalDNS, certManager, awsLoadBalancerController, albIngress, autoScaler, ebs`

  e.  Use the following instanceSelector:

```

instanceSelector: 

  vCPUs: 2

  memory: 4GiB

```

  f. Set `ssh.allow` to `true`

  g, Now save `cluster.yaml` and create the cluster by running: `eksctl create cluster -f cluster.yaml`



While the cluster is getting created:



- Install Helm: `curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash`

- Create a new helm chart to:

  - Create a deployment of otomato/au (a tiny echo http server)

  - Expose it with a service (listens on port 3100)

  - Make it accessible with an ingress



Once the cluster is created - deploy the chart to the cluster.


