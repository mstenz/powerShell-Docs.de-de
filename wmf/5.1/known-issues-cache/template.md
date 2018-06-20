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
><span data-ttu-id="651dc-103">Hinweis: Vorschlag für einen aussagekräftigen Namen und eine Kurzbeschreibung bereitstellen</span><span class="sxs-lookup"><span data-stu-id="651dc-103">Note: provide a proposed descriptive title and a brief description</span></span>

## <a name="example-erroneous-executionpolicy-errors"></a><span data-ttu-id="651dc-104">Beispiel: Fehlerhafte „ExecutionPolicy“-Fehler</span><span class="sxs-lookup"><span data-stu-id="651dc-104">Example: Erroneous ExecutionPolicy errors</span></span> ##
<span data-ttu-id="651dc-105">Unter Windows 7 kann die Verwendung von PowerShell-Modulen und DSC-Ressourcen zu Fehlern führen, die zu „ExecutionPolicy“ gemeldet werden.</span><span class="sxs-lookup"><span data-stu-id="651dc-105">On Windows 7, the use of PowerShell modules and DSC resources may result in errors reported about ExecutionPolicy.</span></span>

### <a name="resolution"></a><span data-ttu-id="651dc-106">Lösung</span><span class="sxs-lookup"><span data-stu-id="651dc-106">Resolution</span></span>

<span data-ttu-id="651dc-107">Legen Sie als Lösung **ExecutionPolicy** auf **RemoteSigned** fest, indem Sie den folgenden Befehl mit erhöhten Rechten in einer PowerShell-Sitzung ausführen (Als Administrator ausführen):</span><span class="sxs-lookup"><span data-stu-id="651dc-107">To resolve, set the **ExecutionPolicy** to **RemoteSigned** by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Set-ExecutionPolicy RemoteSigned
```
