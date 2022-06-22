# Guides and Specifications for Online Verification for Travellers

The original overview document can be found at https://docs.google.com/document/d/1BW-Bn9nf0mtCa8p36nbxt3GYuhy6xuBaG8lIDxi-aNs.

This repo describes the Online Verification for Travellers system which consits of 3 co-operating components. 

* Validation Service - https://github.com/minienw/onlineverification_code
* Wallet - https://github.com/minienw/onlineverification_wallet
* Airline Stub - https://github.com/minienw/airlinestub

In theory, each component can be hosted by seperate parties.

The airline stub is purely for testing and demonstration purposes.

The following are dependencies of the Validation Service:

* DCC Signature Verifier - https://github.com/minienw/onlineverification_dcc_verifier
* DCC Artifact Parser - https://github.com/minienw/onlineverification_dcc_artifact_parser

The busines rules engine (TODO replace binary file dependency with new Maven Repo package dependency) used by the Validation Service is hosted here:

* DCC Business Rules Engine - https://github.com/ehn-dcc-development/eu-dcc-business-rules

# Docker image repository

Images can be found at https://github.com/orgs/minienw/packages which has the uri prefix ghcr.io/minienw/.

Both ghcr.io/minienw/verifier:latest and ghcr.io/minienw/dccparser:latest can be used 'as-is' as part of a docker-compose or kubernetes deployment.

The Wallet can also be deployed 'as-is' in a standalone manner (image TBD!).

For the Validation Service and the Airline Stub, use the images tagged 'latest_noconfig' as the base and locally build configured images to deploy in your environment.

# Deployment scenarios

See the configuration overview document.

The services are dependent on each other. Various URIs dependent on where each component is hosted are used to configure other dependent components. The simplest order (in order of configuration dependencies) to install the components in is:

1. Airline Stub
2. Validation Service
3. Wallet

Multiple Airline Stubs can be deployed to simulate multiple airlines cooperating with the Validation Service and Wallet.

# Kubernetes on Azure

Both Validation Service and Airline Stub repos contain scripts for deploying in a Kubernetes cluster. These 2 services use multiple docker images

(TBD! addition of DCC Artifact Parser to the Validation Service)

Build the cluster using the scripts in the folder 'azurekubernetes', build images configured to operate in the kubernetes environment as described in each repo, then deploy the images to the cluster in the usual way.
