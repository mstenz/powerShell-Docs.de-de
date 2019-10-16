---
title: Benennen einer helpinfo-XML-Datei | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367199"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Benennen einer XML-Datei HelpInfo

In diesem Thema wird das erforderliche Namensformat für die aktualisierbaren Hilfe Informationsdateien erläutert, die häufig als helpinfo-XML-Dateien bezeichnet werden.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Benennen einer XML-Datei HelpInfo

Eine helpinfo-XML-Datei muss einen Namen haben, der das folgende Format hat.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Die Elemente des Namens lauten wie folgt.

ModuleName der Wert der **Name** -Eigenschaft des **ModuleInfo** -Objekts, das vom [Get-Module-](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet zurückgegeben wird.

ModuleGUID der Wert des **GUID** -Schlüssels im Modul Manifest.

Wenn der Modulname beispielsweise "Testmodule" und die Modul-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 ist, lautet der Name der helpinfo-XML-Datei für das Modul wie folgt:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`