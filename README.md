<div align="center">
  <h1> Charts-Helm Repository</h1>
  <p><strong>Source of Truth for Deployment (GitOps)</strong></p>
</div>

<hr />

##  Project Overview
This repository contains the <b>Helm Charts</b> that declare the desired state for deploying our applications in the development and staging environments[cite: 42]. It is managed via <b>ArgoCD</b>, ensuring that the cluster state always matches the configuration defined here[cite: 40].

---

##  Repository Structure
| File/Folder | Purpose |
| :--- | :--- |
| <b>charts/aplicacion/Chart.yaml</b> | Metadata for the Chart including name and version[cite: 44]. |
| <b>charts/aplicacion/values.yaml</b> | <b>The Key File.</b> Contains configuration variables, including the Docker image tag that ArgoCD must deploy[cite: 44]. |

---

##  Guide for DevOps & Infrastructure Team
This repository is the backbone of our deployment strategy and follows strict operational rules:

* <b>No Manual Developer Modification:</b> This repository should not be modified manually by developers[cite: 46].
* <b>Automatic Updates:</b> The GitHub Actions pipeline from the <code>aplicacion-python</code> repository is the <b>only entity</b> allowed to modify the <code>values.yaml</code> file automatically[cite: 47].
* <b>Monitoring:</b> ArgoCD is configured to monitor this repository. Any commit on the monitored branch (e.g., main or staging) will trigger an automatic deployment[cite: 48].
* <b>Manual Overrides:</b> Any necessary manual change to the deployment configuration must be done via a <b>Pull Request</b>, requiring review and approval from the Infrastructure team[cite: 49].

---

##  Points of Customization for ArgoCD Integration
When setting up a new service within this structure, ensure the following are correctly configured:

1.  <b>Repository Path:</b> Verify that the path in the <code>yq</code> command within the <code>aplicacion-python</code> <code>main.yml</code> file points to the correct location of this chart[cite: 52].
2.  <b>Image Tag Key:</b> Ensure the path used by <code>yq</code> to update the tag (e.g., <code>.image.tag</code>) matches the exact key defined in your <code>values.yaml</code>[cite: 53].

<hr />

<div align="center">
  <sub>Managed via <b>ArgoCD</b> | Part of the <a href="https://github.com/juanjosesuarezburgos/aplicacion-python">Python Pipeline</a> Ecosystem</sub>
</div>
