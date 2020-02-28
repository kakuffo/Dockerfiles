
# Orchestration
Orchestration is the automated configuration, coordination, and management 
of computer systems and software. A number of tools exist for automation of server configuration and management, 
including Ansible, Puppet, Salt, Terraform, and AWS CloudFormation.

## Orchestration Steps
Creating a Dockerfile
Building an Image from Dockerfile
Validate if the Image is created and Listed
Optionally upload to docker Hub to share with the world
Start the Container from Image
Create Manifest file for kubernetes
Build and Create a POD from Manifest file
Validate and Monitor the POD creation
Check the newly created POD in Kubernetes DashBoard

## Orchestration Tools
 
## GETTING STARTED

### create

### get

### run

### expose

### delete

## APP MANAGEMENT

### apply
Apply a configuration to a resource by filename or stdin. The resource name must be specified. This resource will be 
created if it doesn't exist yet. To use 'apply', always create the resource initially with either 'apply' or 
'create --save-config'.  JSON and YAML formats are accepted.  Alpha Disclaimer: the --prune functionality is not 
yet complete. Do not use unless you are aware of what the current state is. See https://issues.k8s.io/34274.

#### edit-last-applied
#### set-last-applied
#### view-last-applied

### annotate

### autoscale

### convert

### diff

### edit

### label

### patch

### replace

### rollout
#### history
#### pause
#### restart
#### resume
#### status
#### undo

### scale

### set

#### env
#### image
#### resources
#### selector
#### serviceaccount
#### subject

### wait

## WORKING WITH APPS

### attach

### auth
#### can-i
#### reconcile

### cp

### describe

### exec

### logs

### port-forward

### proxy

### top
#### node
#### pod

## CLUSTER MANAGEMENT

### api-versions

### certificate

### cluster-info

### cordon

### drain

### taint

### uncordon

## KUBECTL SETTINGS AND USAGE

### alpha

### api-resources

### completion

### config

### explain

### kustomize

### options

### plugin

### version

DEPRECATED COMMANDS
rolling-update