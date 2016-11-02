# apigee-cloudfoundry-edgemicro

The purpose of this repository is to spin up a microgateway instance with Bosh.

## Bosh Lite
I used [Bosh lite](https://github.com/cloudfoundry/bosh-lite) to test it.

## Install Bosh CLI
Install the [Bosh cli](https://bosh.io/docs/bosh-cli.html).

## Deploy to Bosh
The following commands assume that you are using Bosh lite. It will setup your bosh lite environment
and it will try to start up a new VM with microgateway.

```
cd apigee-cloudfoundry-edgemicro

bosh target 192.168.50.4 lite

bosh deployment manifest.yml

wget --content-disposition https://bosh.io/d/stemcells/bosh-warden-boshlite-ubuntu-trusty-go_agent

bosh upload stemcell bosh-stemcell-3147-warden-boshlite-ubuntu-trusty-go_agent.tgz

bosh create release --force

bosh upload release

bosh deploy
```

## Current Issues
It copies the Node.js package to the VM, but it doesn't copy the edgemicro package.
I think it is failing after the Node.js package is copied.
