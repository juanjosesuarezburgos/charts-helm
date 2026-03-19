<div align="center">
  <h1></h1>
<hr />

## Project Overview
This repository contains the <b>Helm Charts</b> that define the desired state for our applications across different environments. It acts as the central configuration hub, ensuring that deployments are standardized and version-controlled.

---

## Repository Structure
| File/Folder | Purpose |
| :--- | :--- |
| <b>charts/aplicacion/Chart.yaml</b> | Metadata for the Chart (name, version). |
| <b>charts/aplicacion/values.yaml</b> | <b>The Key File.</b> Contains configuration variables, including the Docker image tag that must be deployed. |

---

## Guide for DevOps & Infrastructure Team
This repository follows a strict operational workflow to maintain environment stability:

* <b>No Manual Developer Modification:</b> To prevent configuration drift, this repository should not be modified manually by application developers.
* <b>Automatic Updates:</b> The GitHub Actions pipeline from the <code>aplicacion-python</code> repository is the <b>primary entity</b> authorized to update the <code>values.yaml</code> file automatically during a release.
* <b>Manual Overrides:</b> Any necessary manual adjustments to the deployment infrastructure must be handled via a <b>Pull Request</b>, requiring a formal review and approval process.
* <b>Deployment Monitoring:</b> This repository serves as the reference for the current live state of the application.

---

## Points of Customization for Integration
When integrating a new service, ensure the following parameters match the automation pipeline:

1.  <b>Repository Path:</b> Verify that the <code>repository:</code> path in the <code>aplicacion-python</code> workflow points correctly to this repository.
2.  <b>Image Tag Key:</b> Ensure the <code>yq</code> command in the pipeline targets the exact key (e.g., <code>.image.tag</code>) defined within your <code>values.yaml</code> file.

<hr />

<div align="center">
  <sub>Part of the <a href="https://github.com/juanjosesuarezburgos/aplicacion-python">Python Pipeline</a> Ecosystem</sub>
</div>
