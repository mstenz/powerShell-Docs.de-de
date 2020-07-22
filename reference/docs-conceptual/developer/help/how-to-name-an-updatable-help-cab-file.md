---
title: Benennen von aktualisierbaren CAB-Hilfedateien
ms.date: 09/12/2016
ms.openlocfilehash: 42486461d92f1f6fcff452a4539edf5be7a66f22
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892998"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a>Benennen von aktualisierbaren CAB-Hilfedateien

In diesem Thema wird das erforderliche Namensformat für die aktualisierbaren Hilfe CAB- `.CAB` Dateien () erläutert.

## <a name="how-to-name-an-updatable-help-cab-file"></a>Benennen von aktualisierbaren CAB-Hilfedateien

Eine aktualisierbare CAB- `.CAB` Datei () muss einen Namen haben, der das folgende Format hat.

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

Die Elemente des Namens lauten wie folgt.

- `<ModuleName>`: Der Wert der **Name** -Eigenschaft des **ModuleInfo** -Objekts, das vom [Get-Module-](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet zurückgegeben wird.
- `<ModuleGUID>`: Der Wert des **GUID** -Schlüssels im Modul Manifest.
- `<UICulture>`: Die Benutzeroberflächen Kultur der Hilfedateien in der CAB-Datei. Dieser Wert muss mit dem Wert eines der **UICulture** -Elemente in der helpinfo-XML-Datei für das Modul identisch sein.

Wenn der Modulname beispielsweise "Testmodule" lautet, ist die Modul-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, und die Benutzeroberflächen Kultur ist "en-US", der Name der CAB-Datei lautet wie folgt:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
