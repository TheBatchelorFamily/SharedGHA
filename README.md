# SharedGHA
A repository for shared github actions

## Workflows

### General Usage
* Unlike a typical github actions workflow, you do not specify the "runs-on" or any environment parameters, as these are provided within the re-usable workflow in this repository. You can also choose to simply inherit the secrets from the local repo that calls the workflow. That configuration is shown below, but you can alternatively map your secrets to the required secrets from the workflow similarly to the other inputs.
  ```yaml
  jobs:
    Workflow_Name:
      uses: TheBatchelorFamily/SharedGHA/.github/workflows/workflow_file.yml@1.0.0
      with:
        inputOne: 'someInput'
        inputTwo: 'someOtherInput'
        inputThree: 'someAdditinoalInput'
      secrets: inherit
  ```

### Container Registration

* Overview
  
  * Authenticates with [Docker Hub](https://hub.docker.com/)
  * Builds the image and applies the supplied container version
  * Scans the image with [Trivy](https://github.com/aquasecurity/trivy) and [Dockle](https://github.com/goodwithtech/dockle) using the [Azure Container-scan](https://github.com/Azure/container-scan) workflow
  * Pushes the image to Docker Hub
  * Builds the image and applies the `latest` tag
  * Pushes the image to Docker Hub with the `latest` tag

* Inputs
  
  See details [here](.github/workflows/container_registration.yml#L6).

### Terraform Deploy

* Overview
  
  The module sets up the security group, the elastic ip, and the route53 entries for www and non-www URLs.

* Inputs
  
  See details [here](.github/workflows/terraform_deploy.yml#L6).
