---
title: Setup an Azure Bicep Dev Environment
date: 2023-12-15 12:01:00 -500
categories: [Azure, Bicep]
tags: [azure,bicep,how to,cli,cloud,employers]     #TAG names should always be lowercase
image:
  path: https://i.imgur.com/WqcVNcC.png
  alt: some alt text
---

<br>

>“Everything is going to be connected to cloud and data... all of this will be mediated by software."<br>- Satya Nadella, Microsoft CEO

<br>

## Setting Up an Azure Bicep Developer Environment

Azure Bicep was announced at Ignite 2020. Bicep is Microsoft's (DSL) Domain-Specific Language that maps 1-to-1 with (ARM) Azure Resource Manager templates. Over the years, ARM templates have become increasingly complex and burdensome. Bicep is Microsoft's answer to this problem. 

[Resources Used](#resources)

## Tasks

- [ ] Install Bicep extension for Visual Studio Code
- [ ] Install Azure CLI
- [ ] Verify Bicep developer environment requirements met

## Install the Bicep Extension for VSCode

Open VSCode and open Extensions. Search for `bicep`.

<img src="https://i.imgur.com/LmTfVCT.png" alt="VSCode bicep extension search results" width="100%" />
_VSCode Bicep Extension search results_

Next, click Install.

<img src="https://i.imgur.com/TvlaCXl.png" alt="VSCode bicep extension install" width="100%" />
_VSCode Bicep Extension install button_

Done.

## Install the Azure CLI*

>In the past, the Bicep CLI was separate from the Azure CLI. Microsoft has made things easier. Per the documentation, "Azure CLI automatically installs the Bicep CLI when a command is executed that needs it."
{: .prompt-info}

Open the link to the MSI for the latest version of the Azure CLI:

[Azure CLI MSI Installer](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli)

Choose the release for your system, most likely the 64-bit option.

<img src="https://i.imgur.com/H1Mbrwf.png" alt="Azure CLI MSI Installer" width="100%" />
_Azure CLI MSI Installer_

Once the installer is downloaded, open and click through (Next, Accept EULA, Install, Finish) the installation.

Done.

## Verify Everything Works

Verify the Azure CLI was installed correctly. Open Powershell and run the `az --version` command.

<img src="https://i.imgur.com/JXV5Rrk.png" alt="Check Azure CLI version" width="100%" />
_Checking the Azure CLI version_

Now, if we try and verify our Bicep version, we get something like this...

<img src="https://i.imgur.com/3DPFB2u.png" alt="Check Bicep CLI version error" width="100%" />
_Azure Bicep CLI version error_

Remember, the "Azure CLI automatically installs the Bicep CLI when a command is executed that needs it." We haven't run any commands that would trigger the  install of the Bicep CLI. The prompt says to run `az bicep install`. Okay.

<img src="https://i.imgur.com/COYxyJ6.png" alt="Azure Bicep CLI install" width="100%" />
_Running Azure Bicep CLI install_

<img src="https://i.imgur.com/jk83EmD.png" alt="Azure Bicep CLI install finished" width="100%" />
_Azure Bicep CLI install finished_

And running `az bicep version` is successful this time.

<img src="https://i.imgur.com/L1JFlh9.png" alt="Check Bicep CLI version again" width="100%" />
_Checking Azure Bicep version again_

>To make sure you have the latest Bicep version you can use the `az bicep upgrade` command.
{: .prompt-tip}

## Tasks

- [x] Install Bicep extension for Visual Studio Code
- [x] Install Azure CLI
- [X] Verify bicep developer environment requirements met

And that's it, all of the Bicep development environment requirements have been met!


### <a id="resources"></a>Resources used in this post ###

1. [Microsoft - Bicep Overview](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview?tabs=bicep)
2. [Cloud with Chris - Introduction to Project Bicep](https://www.cloudwithchris.com/blog/introduction-to-bicep/)
3. [Getting Started with Azure Bicep](https://www.youtube.com/watch?v=77AfsFzTsI4&t)
4. [Microsoft - Install Azure CLI on Windows](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli)