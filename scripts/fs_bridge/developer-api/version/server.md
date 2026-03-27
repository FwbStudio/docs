---
layout:
  width: wide
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
---
# Server

This page documents the server-side version helpers.

`lua
FWB.GetResourceServerVersion(resource)
FWB.GetResourceServerVersionString(resource)
FWB.GetResourceGithubVersion(resource)
FWB.GetResourceGithubVersionString(resource)
FWB.HasLatestVersion(resource)
` 

GitHub version helpers compare the installed resource against the latest FwbStudio release.

