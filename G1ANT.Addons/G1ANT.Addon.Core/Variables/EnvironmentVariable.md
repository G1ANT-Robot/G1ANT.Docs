# environment

## Syntax

```G1ANT
⟦text⟧ = ♥environment⟦index⟧
```

## Description

Provides access to environment variables, where `index` is the name of an [environment variable](https://github.com/G1ANT-Robot/G1ANT.Manual/blob/develop/appendices/environment.md) (e.g., APPDATA, COMPUTERNAME, HOMEDRIVE).

## Example

```G1ANT
dialog ‴Hi, ♥environment⟦USERNAME⟧!‴
dialog ‴Your files are here: ♥environment⟦USERPROFILE⟧‴
```
