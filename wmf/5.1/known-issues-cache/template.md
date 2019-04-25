---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.topic: conceptual
title: Beispielvorlage für das Hochschreiben eines bekannten Problems oder einer Einschränkung
ms.openlocfilehash: 8c1004e16f78913174af2e519e451f6fd9f30ff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055546"
---
 ><span data-ttu-id="dd62e-103">Hinweis: Vorschlag für einen aussagekräftigen Namen und eine Kurzbeschreibung bereitstellen</span><span class="sxs-lookup"><span data-stu-id="dd62e-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="dd62e-104">Beispiel: Fehlerhafte „ExecutionPolicy“-Fehler</span><span class="sxs-lookup"><span data-stu-id="dd62e-104">Example: Erroneous ExecutionPolicy errors</span></span>
<span data-ttu-id="dd62e-105">Unter Windows 7 kann die Verwendung von PowerShell-Modulen und DSC-Ressourcen zu Fehlern führen, die zu „ExecutionPolicy“ gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="dd62e-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="dd62e-106">Lösung</span><span class="sxs-lookup"><span data-stu-id="dd62e-106">Resolution</span></span>

<span data-ttu-id="dd62e-107">Legen Sie als Lösung **ExecutionPolicy** auf **RemoteSigned** fest, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):</span><span class="sxs-lookup"><span data-stu-id="dd62e-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
