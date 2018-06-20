---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: Beispielvorlage für das Hochschreiben eines bekannten Problems oder einer Einschränkung
ms.openlocfilehash: 453d4e40b906ebcab7314f04e138ded271338846
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221934"
---
>Hinweis: Vorschlag für einen aussagekräftigen Namen und eine Kurzbeschreibung bereitstellen

## <a name="example-erroneous-executionpolicy-errors"></a>Beispiel: Fehlerhafte „ExecutionPolicy“-Fehler ##
Unter Windows 7 kann die Verwendung von PowerShell-Modulen und DSC-Ressourcen zu Fehlern führen, die zu „ExecutionPolicy“ gemeldet werden.

### <a name="resolution"></a>Lösung

Legen Sie als Lösung **ExecutionPolicy** auf **RemoteSigned** fest, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):

```powershell
Set-ExecutionPolicy RemoteSigned
```
