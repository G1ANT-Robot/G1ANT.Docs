# environment

## Syntax

```G1ANT
⟦text⟧ = ♥environment⟦index⟧
```

## Description

Provides access to environment variables, where `index` is the name of an [environment variable](../../../appendices/environment.md) (e.g., APPDATA, COMPUTERNAME, HOMEDRIVE).

## Example

```G1ANT
dialog ‴Hi, ♥environment⟦USERNAME⟧!‴
dialog ‴Your files are here: ♥environment⟦USERPROFILE⟧‴
```
