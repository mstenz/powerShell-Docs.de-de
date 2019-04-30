---
ms.date: 06/20/2018
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „PackageManagementSource“
ms.openlocfilehash: e51b5318288bef458567dd4b58d17caaea3ed69b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077584"
---
# <a name="dsc-packagemanagementsource-resource"></a>DSC-Ressource „PackageManagementSource“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0, Windows PowerShell 5.1

Die Ressource **PackageManagementSource** in Windows PowerShell Desired State Configuration (DSC) bietet einen Mechanismus zum Registrieren von Paketverwaltungsquellen auf einem Zielknoten sowie zum Aufheben der Registrierung. **Auf diese Weise registrierte Verwaltungspaketquellen werden im Systemkontext registriert und können vom Systemkonto oder der DSC-Engine verwendet werden.** Diese Ressource erfordert das Modul **PackageManagement**, das unter http://PowerShellGallery.com verfügbar ist.

> [!IMPORTANT]
> Die folgenden Eigenschaftsinformationen gelten nur für das **PackageManagement**-Modul Version 1.1.7.0 oder höher.

## <a name="syntax"></a>Syntax

```
PackageManagementSource [String] #ResourceName
{
    Name = [string]
    ProviderName = [string]
    SourceLocation = [string]
    [DependsOn = [string[]]]
    [Ensure = [string]{ Absent | Present }]
    [InstallationPolicy = [string]{ Trusted | Untrusted }]
    [PsDscRunAsCredential = [PSCredential]]
    [SourceCredential = [PSCredential]]
}
```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft  |  Beschreibung   |
|---|---|
| Name| Gibt den Namen der Paketquelle an, die auf Ihrem System registriert bzw. deren Registrierung aufgehoben werden soll.|
| ProviderName| Gibt den Namen des OneGet-Anbieters an, über den Sie mit der Paketquelle zusammenarbeiten können.|
| SourceLocation| Gibt den URI der Paketquelle an.|
| Ensure| Bestimmt, ob die Paketquelle registriert oder die Registrierung aufgehoben werden soll.|
| InstallationPolicy| Wird von Anbietern wie dem integrierten NuGet-Anbieter verwendet. Bestimmt, ob Sie der Paketquelle vertrauen. Enthält einen der folgenden Werte: „Untrusted“ (Nicht vertrauenswürdig) oder „Trusted“ (Vertrauenswürdig).|
| SourceCredential| Ermöglicht den Zugriff auf das Paket für eine Remotequelle.|

## <a name="example"></a>Beispiel

Dieses Beispiel registriert die Paketquelle http://nuget.org mithilfe der DSC-Ressource **PackageManagementSource**.

```powershell
Configuration PackageManagementSourceTest
{
    PackageManagementSource SourceRepository
    {
        Ensure      = "Present"
        Name        = "MyNuget"
        ProviderName= "Nuget"
        SourceLocation   = "http://nuget.org/api/v2/"
        InstallationPolicy ="Trusted"
    }
}
```