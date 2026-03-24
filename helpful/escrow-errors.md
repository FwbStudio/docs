# Escrow Errors

This page covers common problems related to escrowed resources.

## `syntax error near '<\1>'`

This usually means the escrowed files were damaged during upload or your environment is using outdated artifacts.

Recommended checks:

1. re-download the resource
2. upload it again with a tool such as `WinSCP` or `Bitvise`
3. avoid using tools that may corrupt escrowed files during transfer
4. update your server artifacts to a current recommended version

If the files were already damaged during upload, replacing only one file is usually not enough. Re-upload the full resource cleanly.

## Missing Entitlement Or Access Problems

If the server says you do not have access to the resource:

1. restart the full server after purchase or after adding the resource
2. make sure the server license key matches the account that owns the asset
3. do not delete escrow-related files such as `.fxap` when they are included
4. re-download the resource if escrow files are missing

## Resource Starts But Behaves Like Files Are Missing

If a script starts but key functionality is broken right away:

- check that all escrow files are still present
- check that the upload finished correctly
- check the server console for missing file or parsing errors
- replace the resource with a clean download if needed
