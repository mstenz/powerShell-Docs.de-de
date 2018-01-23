---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC-Ressource „PackageManagementSource“"
ms.openlocfilehash: 1c904c70369a75802484c3c0520df63602760361
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
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

