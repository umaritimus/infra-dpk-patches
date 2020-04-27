# infra-dpk-patches
Custom implmenentation of INFRA-DPK

## Motivation

Since Oracle is delivering INFRA-DPK extra late, I am publishing a set of my patches to supplement the patching logic misdelivered in PeopleTools DPK for Native Windows installations.

## Installation

### Ensure that your `<puppet_base_dir>`\production is a git repository

1. Navigate to your environment where the dpk modules reside
2. Create a git repository (if it already doesn't exist... hint: it should exist because you are good like that)

e.g.

```powershell
Set-Location 'c:\ProgramData\PuppetLabs\code\environments\production'
& git init
```

### Clone `infra-dpk-patches` repo into a subdirectory

1. In the same location, clone `infra-dpk-patches` repository into a subdirectory

e.g. 

```powershell
Set-Location 'c:\ProgramData\PuppetLabs\code\environments\production'
& git clone https://github.com/umaritimus/infra-dpk-patches.git
Get-ChildItem -Path '.\infra-dpk-patches\'
```

### Apply patches

1. Execute `git apply` for the patches to your dpk installation

e.g. to Apply all patches from `infra-dpk-patches` repo, 

```powershell
Set-Location 'c:\ProgramData\PuppetLabs\code\environments\production'
Get-ChildItem .\infra-dpk-patches\*.patch | ForEach-Object {
    ${patch} = ${_}.Name
    Write-Output "Applying ${patch}"
    & git apply ".\infra-dpk-patches\${patch}"  --verbose
}
```
