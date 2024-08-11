# Terraform Glossary

## HCP Terraform
HCP Terraform builds on Terraform features by managing Terraform runs in a consistent and reliable environment instead of on your local machine.  It securely stores state and secret data, and can connect to version control systems so that you can develop your infrastructure using a workflow similar to application development.

## HCP Terraform Workspaces
HCP Terraform Workspaces represent all of the collections of infrastructure in an organization.  They are also a major component of role-based access in HCP Terraform.  You can grant individual users and user groups permissions for one or more workspaces that dictate whether they can manage variables, perform runs, etc.  You cannot manage resources in HCP Terraform without creating at least one workspace.

## Organizations
Organizations are a shared space for one or more teams to collaborate on workspaces.
