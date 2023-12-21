---
title: Install Azure Bicep
date: 2023-12-15 12:01:00 -500
categories: [Azure, Bicep]
tags: [azure,bicep,how to,cli,cloud]     #TAG names should always be lowercase
---

<br>

>“Everything is going to be connected to cloud and data... all of this will be mediated by software."<br>- Satya Nadella, Microsoft CEO

<br>

## Setup a Bicep Developer Environment

Azure Bicep was announced at Ignite 2020. Bicep is Microsoft's (DSL) Domain-Specific Language that maps 1-to-1 with (ARM) Azure Resource Manager templates. Over the years, ARM templates have become increasingly complex and burdensome. Bicep is Microsoft's answer to this problem. 

[Resources Used](#resources)

## Tasks

- [ ] Install Bicep extension for Visual Studio Code
- [ ] Install Azure CLI
- [ ] Verify bicep developer environment requirements met

## Difficulty Level 
- [X] [ ] [ ] [ ] [ ]

1. Install the Bicep Extension for VSCode

Open VSCode and open Extensions. Search for *bicep*.

<img src="https://i.imgur.com/LmTfVCT.png" alt="VSCode bicep extension search results" width="100%" />
_VSCode Bicep Extension search results_



Next, click Install.

<img src="https://i.imgur.com/TvlaCXl.png" alt="VSCode bicep extension install" width="100%" />

Done.

## Tasks

- [x] Install Bicep extension for Visual Studio Code
- [ ] Install Azure CLI
- [ ] Verify bicep developer environment requirements met

2. Next, we need to install the Azure CLI.*

<info>In the past, the Bicep CLI was separate from the Azure CLI. Microsoft has made things easier. Per the documentation, "Azure CLI automatically installs the Bicep CLI when a command is executed that needs it."</info>

Open the link to the MSI for the latest version of the Azure CLI:

https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli

Choose the release for your system, most likely the 64-bit option.

<img src="https://i.imgur.com/H1Mbrwf.png" alt="Azure CLI MSI Installer" width="100%" />

Once the installer is downloaded, open and click through (Next, Accept EULA, Install, Finish) the installation.

Done.

## Tasks

- [x] Install Bicep extension for Visual Studio Code
- [x] Install Azure CLI
- [ ] Verify bicep developer environment requirements met

3. Lastly, verify everything needed to author Bicep files from VSCode.

Verify the Azure CLI was installed correctly. Open Powershell and run the *az --version* command.

<img src="https://i.imgur.com/JXV5Rrk.png" alt="Check Azure CLI version" width="100%" />

Now, if we try and verify our Bicep version, we get something like this...

<img src="https://i.imgur.com/3DPFB2u.png" alt="Check Bicep CLI version error" width="100%" />

Remember, the "Azure CLI automatically installs the Bicep CLI when a command is executed that needs it." We haven't run any commands that would automatically install the Bicep CLI. The prompt says to run *az bicep install*. Okay.

<img src="https://i.imgur.com/COYxyJ6.png" alt="Check Bicep CLI version error" width="100%" />

<img src="https://i.imgur.com/jk83EmD.png" alt="Check Bicep CLI version error" width="100%" />

And running *az bicep version* is successful this time.

<img src="https://i.imgur.com/L1JFlh9.png" alt="Check Bicep CLI version error" width="100%" />

<tip>To make sure you have the latest Bicep version you can use the *az bicep upgrade* command.</tip>

## Tasks

- [x] Install Bicep extension for Visual Studio Code
- [x] Install Azure CLI
- [X] Verify bicep developer environment requirements met

And that's it, we have successfully verified all the requirements are met.


### <a id="resources"></a>Resources used in this post ###

1. [Microsoft - Bicep Overview](https://learn.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview?tabs=bicep)
2. [Cloud with Chris - Introduction to Project Bicep](https://www.cloudwithchris.com/blog/introduction-to-bicep/)
3. [Getting Started with Azure Bicep](https://www.youtube.com/watch?v=77AfsFzTsI4&t)
4. [Microsoft - Install Azure CLI on Windows](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-windows?tabs=azure-cli)