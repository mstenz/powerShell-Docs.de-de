---
title: Benennen der CAB-Datei für eine aktualisierbare Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367159"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Benennen von aktualisierbaren CAB-Hilfedateien

In diesem Thema wird das erforderliche Namensformat für den aktualisierbaren Hilfe Schrank () erläutert. CAB-Dateien.

## <a name="how-to-name-an-updatable-help-cab-file"></a>Benennen von aktualisierbaren CAB-Hilfedateien

Eine aktualisierbare CAB-(. CAB) muss ein Name im folgenden Format vorliegen.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Die Elemente des Namens lauten wie folgt.

ModuleName der Wert der **Name** -Eigenschaft des **ModuleInfo** -Objekts, das vom [Get-Module-](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet zurückgegeben wird.

ModuleGUID der Wert des **GUID** -Schlüssels im Modul Manifest.

UICulture die Benutzeroberflächen Kultur der Hilfedateien in der CAB-Datei. Dieser Wert muss mit dem Wert eines der **UICulture** -Elemente in der helpinfo-XML-Datei für das Modul identisch sein.

Wenn der Modulname beispielsweise "Testmodule" lautet, ist die Modul-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, und die Benutzeroberflächen Kultur ist "en-US", der Name der CAB-Datei lautet wie folgt:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`