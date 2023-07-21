# Red Hat OpenShift Data Science - Licence plate recognition workshop

https://redhat-scholars.github.io/rhods-lp-workshop/rhods-lp-workshop/index.html

## Extend Pipeline to AAP

Image can be deployed outside of OpenShift to Edge devices. 
Here are the steps to extend pipeline to do that.

- Authenticate default Service Account to push to registry
  - Create robot account on quay.io and download as k8s secret
  - Create secret in OCP
  - Link secret with SA pipeline
    - `oc secrets link pipeline secret-name --for=pull,mount`
- Push image to external registry (quay.io in this example)
  - Edit PipelineRun to include
- Create Secret with Ansible Controller credentials, see [this example](./deploy/OpenShift/secret.template.yml).
  - `oc apply -f secret.yml`

## Next steps

- implement deployment to edge device via AAP
  - Create AAP Job Template to deploy image to RHEL Edge device
- Update pipeline to:
  - copy image to quay
  - call AAP to deploy image to edge

### Creating pipeline for AAP

- Add pipeline to project repo
- Add task to connect to AAP
- Add Secret to connect to AAP
