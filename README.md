# Guides and Specifications for Online Verification for Travellers

This repo describes the Online Verification for Travellers system which consits of 3 co-operating components. 

* Validation Service - https://github.com/minienw/onlineverification_code
* Wallet - https://github.com/minienw/HTMLwallet2.git
* Airline Stub - https://github.com/minienw/airlinestub

In theory, each component can be hosted by seperate parties.

The airline stub is purely for testing and demonstration purposes.

# Docker image repository..

Currently at docker.io/stevekellaway. Migrating to Github.

Use the latest_noconfig-tagged images as the base. See individual repos for building fully configured images.

# Deployment scenarios

See the configuration overview document.

The services are dependent on each other. Various URIs dependent on where each component is hosted are used to configure other dependent components. The simplest order (in order of configuration dependencies) to install the components in is:

1. Wallet
2. Airline Stub
3. Validation Service

## Docker

//TODO

Suitable for development and testing purposes.

See docker compose scripts in each repository.

# Kubernetes on Azure

//TODO

Deploy each component as a seperate Kubernetes cluster.

Build the cluster using the scripts in the folder 'azurekubernetes'

Build configured images as described in each repo.

Deploy the images to the cluster...
