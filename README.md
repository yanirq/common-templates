[![Build Status](https://travis-ci.com/fabiand/common-templates.svg?branch=master)](https://travis-ci.com/fabiand/common-templates)

A set of OpenShift Templates to create KubeVirt VMs.

# Overview

All VMs are provided as [OpenShift templates](https://docs.okd.io/latest/dev_guide/templates.html).
These templates can be used straight forward with OpenShift itself, or they
can be transformed into regular objects for use with Kubernetes.

Every template (if not noted otherwise) has two parameters:

1. `NAME`: The name of the VM to be created
1. `PVCNAME`: The name of the PVC which holds the disk image to be run

Manually transforming a tempalte into a list of objects can be done by using
[`oc`](https://github.com/openshift/origin/releases) - the OpenShift client tool:

```bash
oc process --local \
  -o yaml \
  -f "templates/$TEMPLATE_NAME" \
  NAME=the-vmname \
  PVCNAME=the-pvcname
```

If the object shsall be created right away then the output can be piped to
`kubectl`:

```bash
oc process … | kubectl apply -f -
```

# How to use
## Microsoft Windows Server 2012 R2 (win2k12r2)

This template can be used for "Microsoft Windows Server 2012 R2" and other
Windows versions.

