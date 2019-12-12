---
title: AccessDbProviderSample01-Code Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 22cfbc63bd369ebcb2fd8a0d0e8d1995941bbb0f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74418003"
---
# <a name="accessdbprovidersample01-code-sample"></a>AccessDbProviderSample01-Codebeispiel

Der folgende Code zeigt die Implementierung des Windows PowerShell-Anbieters, der unter [Erstellen eines einfachen Windows PowerShell-Anbieters](./creating-a-basic-windows-powershell-provider.md)beschrieben wird. Diese Implementierung stellt Methoden zum Starten und Beenden des Anbieters bereit und stellt zwar keine Mittel für den Zugriff auf einen Datenspeicher oder zum Abrufen oder Festlegen der Daten im Datenspeicher bereit, bietet jedoch die Grundfunktionen, die von allen Anbietern benötigt werden.

> [!NOTE]
> Sie können die C# Quelldatei (AccessDBSampleProvider01.cs) für diesen Anbieter herunterladen, indem Sie das Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3,0-Laufzeitkomponenten verwenden. Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladenen Quelldateien stehen im **\<PowerShell-Beispiele >** Verzeichnis zur Verfügung.
>
> Weitere Informationen zu anderen Windows PowerShell-Anbieter Implementierungen finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell-Programmier Handbuch](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
