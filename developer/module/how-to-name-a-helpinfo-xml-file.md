---
title: 'Gewusst wie: Benennen Sie eine HelpInfo-XML-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: 462cd7bd486a5924bb2bc43e0ac8d1558e30e657
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794806"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Benennen einer XML-Datei HelpInfo

In diesem Thema wird erläutert, das Format der erforderliche Name für die aktualisierbare Hilfe-Informationen-Dateien, die so genannte HelpInfo XML-Dateien.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Benennen einer XML-Datei HelpInfo

Eine HelpInfo XML-Datei muss es sich um einen Namen mit dem folgenden Format haben.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Die Elemente mit dem Namen sind wie folgt aus.

ModuleName den Wert von der **Namen** Eigenschaft der **ModuleInfo** -Objekt, die [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) -Cmdlet wird zurückgegeben.

ModuleGUID den Wert von der **GUID** -Schlüssels im modulmanifest.

Beispielsweise wäre wenn "TestModule" ist, und die Modul-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 ist, der Namen der HelpInfo XML-Datei für das Modul:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`