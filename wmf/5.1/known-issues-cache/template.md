---
title: "Beispielvorlage für das Hochschreiben eines bekannten Problems oder einer Einschränkung"
contributor: 
ms.openlocfilehash: e3b98044902cb6665e06582c8259bd5defd6f2ca
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
>Hinweis: Vorschlag für einen aussagekräftigen Namen und eine Kurzbeschreibung bereitstellen

## <a name="example-erroneous-executionpolicy-errors"></a>Beispiel: Fehlerhafte „ExecutionPolicy“-Fehler ##
Unter Windows 7 kann die Verwendung von PowerShell-Modulen und DSC-Ressourcen zu Fehlern führen, die zu „ExecutionPolicy“ gemeldet werden.

### <a name="resolution"></a>Lösung

Legen Sie als Lösung **ExecutionPolicy** auf **RemoteSigned** fest, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):

```powershell
Set-ExecutionPolicy RemoteSigned
```
