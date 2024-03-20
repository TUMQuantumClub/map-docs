# Marauder's map documentation

This repository is used to define the communication schema for the marauder's map project.

## Versioning

This repository is still in active development and breaking changes might occur without notice. Once version v.1.0.0 is released, changes will be annotated.
Between minor versions, a server shall offer backwards-compatibility for all endpoints. However, some fields in the graphql schema may be marked as deprecated.

A server may only offer a single major version. It is reccomended for all clients and servers to always use the highest major version.
