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
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857826"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a>Benennen einer XML-Datei HelpInfo

In diesem Thema wird erläutert, das Format der erforderliche Name für die aktualisierbare Hilfe-Informationen-Dateien, die so genannte HelpInfo XML-Dateien.

## <a name="how-to-name-a-helpinfo-xml-file"></a>Benennen einer XML-Datei HelpInfo

Eine HelpInfo XML-Datei muss es sich um einen Namen mit dem folgenden Format haben.

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

Die Elemente mit dem Namen sind wie folgt aus.

ModuleName den Wert von der **Namen** Eigenschaft der **ModuleInfo** -Objekt, die [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) -Cmdlet wird zurückgegeben.
Der Wert des der **Namen** Eigenschaft der **ModuleInfo** -Objekt, die [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) -Cmdlet zurückgegeben.

ModuleGUID den Wert von der **GUID** -Schlüssels im modulmanifest.

Beispielsweise wäre wenn "TestModule" ist, und die Modul-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 ist, der Namen der HelpInfo XML-Datei für das Modul:

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`