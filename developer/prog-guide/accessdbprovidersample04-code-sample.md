---
title: Codebeispiel AccessDbProviderSample04 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9374c4a-e499-4516-9eb6-107c59df98d9
caps.latest.revision: 7
ms.openlocfilehash: 43f01b9cd6af3ab6c26f88ee0c1e9269499b2bc3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081953"
---
# <a name="accessdbprovidersample04-code-sample"></a>AccessDbProviderSample04-Codebeispiel

Der folgende Code zeigt die Implementierung der Windows PowerShell-Anbieter, die in beschriebenen [erstellen eine Windows PowerShell-Containeranbieter](./creating-a-windows-powershell-container-provider.md). Dieser Anbieter funktioniert in Datenspeichern mit mehreren Ebenen. Für diesen Typ des Datenspeichers die oberste Ebene des Speichers die Stamm-Elemente enthält, und jeder nachfolgenden Ebene wird als Knoten der untergeordneten Elemente bezeichnet. Dadurch, dass des Benutzers auf diesen untergeordneten Knoten arbeiten, kann Benutzer über den Data Store hierarchisch interagieren.

## <a name="code-sample"></a>Codebeispiel

[!code-csharp[AccessDBProviderSample04.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample04/AccessDBProviderSample04.cs#L11-L1635 "AccessDBProviderSample04.cs")]

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)