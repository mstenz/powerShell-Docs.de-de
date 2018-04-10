---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Beispielvorlage für das Hochschreiben eines bekannten Problems oder einer Einschränkung
ms.openlocfilehash: cecf31127aaa1942471877a2056230ab592bd095
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
><span data-ttu-id="288cb-103">Hinweis: Vorschlag für einen aussagekräftigen Namen und eine Kurzbeschreibung bereitstellen</span><span class="sxs-lookup"><span data-stu-id="288cb-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="288cb-104">Beispiel: Fehlerhafte „ExecutionPolicy“-Fehler</span><span class="sxs-lookup"><span data-stu-id="288cb-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="288cb-105">Unter Windows 7 kann die Verwendung von PowerShell-Modulen und DSC-Ressourcen zu Fehlern führen, die zu „ExecutionPolicy“ gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="288cb-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="288cb-106">Lösung</span><span class="sxs-lookup"><span data-stu-id="288cb-106">Resolution</span></span>

<span data-ttu-id="288cb-107">Legen Sie als Lösung **ExecutionPolicy** auf **RemoteSigned** fest, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):</span><span class="sxs-lookup"><span data-stu-id="288cb-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```