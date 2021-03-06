# Supported targets

Currently these services are supported as (git) targets:

## Gitlab User (public repositories only)

Currently only public repositories are supported as a Gitlab target (authentication is required to create a Gitlab repository and on creating a repository it will also copy the description from Github automatically):

``` json
{
    "target": "https://gitlab.com/<github user>",
    "accessToken": {
        "source": "https://<keyvault name>.vault.azure.net",
        "secretName": "MyGitlabPAT"
    }
}
```

Required Gitlab scopes on the access token: **api**

## Azure DevOps Project

Azure DevOps projects can be private (default) or public. It is up to you to configure this in the [settings](https://docs.microsoft.com/azure/devops/organizations/public/make-project-public)

Either way authentication is required to create repositories.

``` json
{
    "target": "https://dev.azure.com/<account name>/<project name>",
    "accessToken": {
        "source": "https://<keyvault name>.vault.azure.net",
        "secretName": "MyDevOpsGitPAT"
    }
}
```

Required permissions on the Azure DevOps access token: **Code (read, write & manage)**

## Entire Azure DevOps organization

This copies the entire organization structure (project & repositories). It only copies the repository content, no work items/builds/etc. are mirrored.

**Note:** When using an Azure DevOps organization as a target then you must also use an Azure DevOps organization as the source.

``` json
{
    "target": "https://dev.azure.com/<account name>/*",
    "accessToken": {
        "source": "https://<keyvault name>.vault.azure.net",
        "secretName": "MyDevOpsGitPAT"
    }
}
```

Required permissions on the Azure DevOps access token: **Code (read, write & manage), Project and Team (Read, write, & manage)**

## Access token

See [access token](Access%20token.md) for documentation on the access token syntax.