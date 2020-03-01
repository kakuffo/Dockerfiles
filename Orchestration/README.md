
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
 
## create
### Create a resource from a file or from stdin.
```Shell
$ create -f FILENAME
```
Create a pod using the data in pod.json.
```Shell
kubectl create -f ./pod.json
```
Create a pod based on the JSON passed into stdin.
```Shell
cat pod.json | kubectl create -f -
```
Edit the data in docker-registry.yaml in JSON then create the resource using the edited data.
```Shell
cat pod.json | kubectl create -f -
```
kubectl create -f docker-registry.yaml --edit -o json

|:Name	|:Shorthand|:Default|:	Usage    |
|:------|:---------|:-------|:-----------|
allow-missing-template-keys		true	If true, ignore any errors in templates when a field or map key is missing in the template. Only applies to golang and jsonpath output formats.
dry-run		false	If true, only print the object that would be sent, without sending it.
edit		false	Edit the API resource before creating
filename	f	[]	Filename, directory, or URL to files to use to create the resource
kustomize	k		Process the kustomization directory. This flag can't be used together with -f or -R.
output	o		Output format. One of: json|yaml|name|go-template|go-template-file|template|templatefile|jsonpath|jsonpath-file.
raw			Raw URI to POST to the server. Uses the transport specified by the kubeconfig file.
record		false	Record current kubectl command in the resource annotation. If set to false, do not record the command. If set to true, record the command. If not set, default to updating the existing annotation value only if one already exists.
recursive	R	false	Process the directory used in -f, --filename recursively. Useful when you want to manage related manifests organized within the same directory.
save-config		false	If true, the configuration of current object will be saved in its annotation. Otherwise, the annotation will be unchanged. This flag is useful when you want to perform kubectl apply on this object in the future.
selector	l		Selector (label query) to filter on, supports '=', '==', and '!='.(e.g. -l key1=value1,key2=value2)
template			Template string or path to template file to use when -o=go-template, -o=go-template-file. The template format is golang templates [http://golang.org/pkg/text/template/#pkg-overview].
validate		true	If true, use a schema to validate the input before sending it
windows-line-endings		false	Only relevant if --edit=true. Defaults to the line ending native to your platform.
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

#### current-context

#### delete-cluster

#### delete-context

#### get-clusters

#### get-contexts

#### rename-context

#### set

#### set-cluster

#### set-context

#### set-credentials

#### unset

#### use-context

### view

### explain

### kustomize

### options

### plugin

### version

# Workflow

Gubernator Dashboard - View incoming and outgoing Pull Requests that require your attention.
Prow - Kubernetes CI/CD System.
Tide - Prow plugin that manages merges and tests. Tide Dashboard
Bot commands - Commands used to interact with Kubernetes Bots (examples: /cc, /lgtm, and /retest)
GitHub labels - List of labels used throughout the Kubernetes Project
Kubernetes Code Search, maintained by @dims

# Tests

Prow - Kubernetes CI/CD System.
Test Grid - View historical tests and their associated information.
Triage Dashboard - Aggregates similar failures together for better troubleshooting.
Velodrome - Dashboard to track job and test health.