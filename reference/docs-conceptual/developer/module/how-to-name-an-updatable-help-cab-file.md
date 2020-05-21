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
ms.openlocfilehash: a253f98d213f797a659affb1560907bb99a045d3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560558"
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
