---
title: Windows PowerShell-Sitzungs Status | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Cmdlets [PowerShell], session state
- session state [PowerShell]
ms.assetid: 74912940-2b10-4a76-b174-6d035d71c02b
caps.latest.revision: 8
ms.openlocfilehash: fa207130bbb120750780bb0aa9b32150a32daaa2
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369099"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell-Sitzungszustand

Der Sitzungs Status bezieht sich auf die aktuelle Konfiguration einer Windows PowerShell-Sitzung oder eines Windows PowerShell-Moduls. Eine Windows PowerShell-Sitzung ist die Betriebsumgebung, die interaktiv vom Befehlszeilen Benutzer oder Programm gesteuert von einer Host Anwendung verwendet wird. Der Sitzungszustand für eine Sitzung wird als globaler Sitzungszustand bezeichnet.

Aus Sicht des Entwicklers bezieht sich eine Windows PowerShell-Sitzung auf die Zeit zwischen dem Öffnen eines Windows PowerShell-Runspace durch eine Host Anwendung und dem Schließen des Runspace. Anders betrachtet, ist die Sitzung die Lebensdauer einer Instanz der Windows PowerShell-Engine, die aufgerufen wird, während der Runspace vorhanden ist.

## <a name="module-session-state"></a>Modul Sitzungs Status

Modul Sitzungs Zustände werden immer dann erstellt, wenn das Modul oder eines seiner in die Sitzung importierten Module importiert wird. Wenn ein Modul ein Element, z. b. ein Cmdlet, eine Funktion oder ein Skript, exportiert, wird dem globalen Sitzungs Status der Sitzung ein Verweis auf dieses Element hinzugefügt. Wenn das Element ausgeführt wird, wird es jedoch innerhalb des Sitzungs Status des Moduls ausgeführt.

## <a name="session-state-data"></a>Sitzungszustandsdaten

Sitzungszustandsdaten können öffentlich oder privat sein. Öffentliche Daten sind für Aufrufe außerhalb des Sitzungs Zustands verfügbar, während private Daten nur für Anrufe innerhalb des Sitzungs Zustands verfügbar sind. Ein Modul kann z. b. über eine private Funktion verfügen, die nur vom Modul oder nur intern von einem öffentlichen, exportierten Element aufgerufen werden kann. Dies ist vergleichbar mit den privaten und öffentlichen Membern eines .NET Framework Typs.

Sitzungszustandsdaten werden von der aktuellen Instanz der Ausführungs-Engine innerhalb des Kontexts der aktuellen Windows PowerShell-Sitzung gespeichert. Sitzungszustandsdaten bestehen aus den folgenden Elementen:

- Pfadinformationen

- Laufwerks Informationen

- Informationen zum Windows PowerShell-Anbieter

- Informationen zu den importierten Modulen und verweisen auf die Modul Elemente (z. b. Cmdlets, Funktionen und Skripts), die vom Modul exportiert werden. Diese Informationen und diese Verweise gelten nur für den globalen Sitzungs Status.

- Informationen zu Sitzungs Zustandsvariablen

## <a name="accessing-session-state-data-within-cmdlets"></a>Zugreifen auf Sitzungszustandsdaten innerhalb von Cmdlets

Cmdlets können auf Sitzungszustandsdaten entweder indirekt über die [System. Management. Automation. PSCmdlet. SessionState *](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) -Eigenschaft der Cmdlet-Klasse oder direkt über die [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) -Klasse zugreifen. Die [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) -Klasse stellt Eigenschaften bereit, die verwendet werden können, um unterschiedliche Typen von Sitzungszustandsdaten zu untersuchen.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. PSCmdlet. SessionState](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System. Management. Automation. SessionState? Displayproperty = FullName](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell-Cmdlets](./cmdlet-overview.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
