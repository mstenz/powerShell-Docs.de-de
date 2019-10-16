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
ms.openlocfilehash: 429339a86b44bfa53302329fe1e21f6f91c52b42
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360549"
---
# <a name="accessdbprovidersample01-code-sample"></a>AccessDbProviderSample01-Codebeispiel

Der folgende Code zeigt die Implementierung des Windows PowerShell-Anbieters, der unter [Erstellen eines einfachen Windows PowerShell-Anbieters](./creating-a-basic-windows-powershell-provider.md)beschrieben wird. Diese Implementierung stellt Methoden zum Starten und Beenden des Anbieters bereit und stellt zwar keine Mittel für den Zugriff auf einen Datenspeicher oder zum Abrufen oder Festlegen der Daten im Datenspeicher bereit, bietet jedoch die Grundfunktionen, die von allen Anbietern benötigt werden.

> [!NOTE]
> Sie können die C# Quelldatei (AccessDBSampleProvider01.cs) für diesen Anbieter herunterladen, indem Sie das Windows Software Development Kit für Windows Vista und Microsoft .NET Framework 3,0-Laufzeitkomponenten verwenden. Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladenen Quelldateien sind in den **\<powershell-Beispielen >** Verzeichnis verfügbar.
>
> Weitere Informationen zu anderen Windows PowerShell-Anbieter Implementierungen finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md).

## <a name="code-sample"></a>Code Beispiel

[!code-csharp[AccessDBProviderSample01.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell-Programmier Handbuch](./windows-powershell-programmer-s-guide.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
