---
title: "DSC-Ressource „PackageManagementSource“"
ms.date: 
keywords: powershell,DSC
description: 
ms.topic: article
author: brywang-msft
manager: kriscv
ms.prod: powershell
ms.openlocfilehash: 22e61490e7b3f98335334a2703ec9639cbdaa87e
ms.sourcegitcommit: 89e7ae30faff5f96641fc72764bdc76e0e257bc2
translationtype: HT
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
