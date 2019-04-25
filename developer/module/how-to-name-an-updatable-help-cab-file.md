---
title: 'Gewusst wie: Benennen Sie eine aktualisierbare Hilfe CAB-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082361"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Benennen von aktualisierbaren CAB-Hilfedateien

In diesem Thema wird erläutert, das erforderliche Format für die aktualisierbare Hilfe CAB-Datei (. CAB-Datei)-Dateien.

## <a name="how-to-name-an-updatable-help-cab-file"></a>Benennen von aktualisierbaren CAB-Hilfedateien

Aktualisierbare CAB-Datei (. CAB-Datei)-Datei muss es sich um einen Namen mit dem folgenden Format aufweisen.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Die Elemente mit dem Namen sind wie folgt aus.

ModuleName den Wert von der **Namen** Eigenschaft der **ModuleInfo** -Objekt, die [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) -Cmdlet wird zurückgegeben.

ModuleGUID den Wert von der **GUID** -Schlüssels im modulmanifest.

Der UICulture-UI-Kultur der Hilfedateien in der CAB-Datei. Dieser Wert muss dem Wert eines entsprechen den **UICulture** Elemente in der HelpInfo-XML-Datendatei für das Modul.

Beispielsweise ist der Modulname "TestModule", die Modul-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, und die UI-Kultur ist "En-US", der Namen der CAB-Datei:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`