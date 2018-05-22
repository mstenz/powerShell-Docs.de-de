---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Funktion zum Abfragen von Knoteninformationen vom Pullserver
ms.openlocfilehash: 069fc79a79fbd5f75bcce27f7f0bd95af0d7b1ad
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-function-to-query-node-information-from-pull-server"></a>DSC-Funktion zum Abfragen von Knoteninformationen vom Pullserver

```powershell
function QueryNodeInformation
{
Param (
       [string] $Uri =
"http://localhost:7070/PSDSCComplianceServer.svc/Status",
       [string] $ContentType = "application/json"
     )

  Write-Host "Querying node information from pull server URI  = $Uri" -ForegroundColor Green

  Write-Host "Querying node status in content type  = $ContentType " -ForegroundColor Green

   $response = Invoke-WebRequest -Uri $Uri -Method Get -ContentType $ContentType -UseDefaultCredentials -Headers
    @{Accept = $ContentType}

   if($response.StatusCode -ne 200)
 {
     Write-Host "node information was not retrieved." -ForegroundColor Red
 }

 $jsonResponse = ConvertFrom-Json $response.Content

  return $jsonResponse
}
```

Ersetzen Sie den `Uri`-Parameter durch den URI Ihres Pullservers. Wenn Sie die Knoteninformationen im XML-Format wünschen, legen Sie `ContentType` auf `application/xml` fest.

Zum Abrufen von Knoteninformationen aus dem `$json`-Parameter verwenden Sie Folgendes:

```powershell
$json = QueryNodeInformation –Uri http://localhost:7070/PSDSCComplianceServer.svc/Status

$json.value | Format-Table TargetName, ConfigurationId, ServerChecksum, NodeCompliant, LastComplianceTime, StatusCode
```