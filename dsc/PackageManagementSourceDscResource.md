---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „PackageManagementSource“"
ms.openlocfilehash: 80d157aff5bf7685a797baaf6a26215f02473096
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC-Ressource „PackageManagementSource“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource **PackageManagementSource** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Registrieren von Paketverwaltungsquellen auf einem Zielknoten sowie zum Aufheben der Registrierung. **Auf diese Weise registrierte Verwaltungspaketquellen werden im Systemkontext registriert und können vom Systemkonto oder DSC-Modul verwendet werden.** Diese Ressource erfordert das Modul **PackageManagement**, das unter „http://PowerShellGallery.com“ verfügbar ist.

## <a name="syntax"></a>Syntax

```
PSModule [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ InstallationPolicy = [string] ]
    [ ProviderName = [string] ]
    [ SourceUri = [string] ]
    [ SourceCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Eigenschaften
|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Name| Gibt den Namen der Paketquelle an, die auf Ihrem System registriert bzw. deren Registrierung aufgehoben werden soll.| 
| Ensure| Bestimmt, ob die Paketquelle registriert oder die Registrierung aufgehoben werden soll.| 
| InstallationPolicy| Bestimmt, ob Sie der Paketquelle vertrauen. Entweder „Nicht vertrauenswürdig“, oder „Vertrauenswürdig“.| 
| ProviderName| Gibt den Namen des OneGet-Anbieters an, über den Sie mit der Paketquelle zusammenarbeiten können.| 
| SourceUri| Gibt den URI der Paketquelle an.| 
| SourceCredential| Ermöglicht den Zugriff auf das Paket für eine Remotequelle.| 

## <a name="example"></a>Beispiel

Dieses Beispiel registriert die Paketquelle „http://nuget.org“ mit der DSC-Ressource **PackageManagementSource**.

```powershell
Configuration PackageManagementSourceTest
{    
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present" 
        Name        = "MyNuget" 
        ProviderName= "Nuget" 
        SourceUri   = "http://nuget.org/api/v2/"   
        InstallationPolicy ="Trusted" 
    }
}
```

