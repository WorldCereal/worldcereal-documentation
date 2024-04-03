
# Authentication

All authentication in WorldCereal is done via OIDC, the most widely adopted standard at this time, and also the standard
used within various openEO deployments (openEO platform, CDSE). It was also used in phase 1 of the project.

WorldCereal does not have a requirement to maintain a user credentials database, so we opt to rely on one or more external
identity providers (IdP). This results in extra features such as Single Sign-On (SSO) and enhanced security. It also
reduces the operational costs, which increases sustainability after project end.

# Authorization

Authorization rules are fairly limited, and depend on the use case and component.

## Viewing demonstrator datasets

The WorldCereal viewer can be used anonymously, no authorization needed.

## Data dissemination

Global demonstrator products are free and open data. Strictly speaking no authorization is needed, but dissemination and catalog
services may require authentication to prevent abuse.

## Custom processing

Users can launch jobs to train models or to generate products. This will be done via the CDSE openEO instance.
In general, there's two options here:

- The user has CDSE account, and uses CDSE public service directly. This option is already possible today, as it does not require anything special.
- The user uses the openEO UDPs, as onboarded into ESA NoR, and wants to run the service with NoR sponsoring. This option is foreseen to be supported by APEx, who wil handle integration with the (new) NoR. The IdP is still to be determined.

## Reference data uploading

Users can upload reference data after logging in. Their reference data is either private or public, or private and shared with
WorldCereal, but can not be shared with other users. 
This means that should simply be able to login, via the IdP. Currently Terrascope is used here as IdP. No custom authorization rules are needed.

For RDM power users, the RDM should allow simple configuration of a limited set of users.