---
title: Windows PowerShell-Sitzungsstatus | Microsoft-Dokumentation
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066973"
---
# <a name="windows-powershell-session-state"></a>Windows PowerShell-Sitzungszustand

Sitzungsstatus bezieht sich auf die aktuelle Konfiguration einer Windows PowerShell-Sitzung oder dieses Moduls. Eine Windows PowerShell-Sitzung ist die betriebsumgebung, die interaktiv vom Benutzer Befehlszeile oder programmgesteuert von einer hostanwendung verwendet wird. Der Sitzungszustand für eine Sitzung wird als den globalen Sitzungsstatus bezeichnet.

Bezieht sich aus Sicht eines Entwicklers bietet eine Windows PowerShell-Sitzung auf den Zeitraum zwischen, wenn eine hostanwendung mit einen Windows PowerShell-Runspace geöffnet wird und wenn den Runspace geschlossen wird. Eine andere Möglichkeit haben, ist die Sitzung der Lebensdauer einer Instanz von der Windows PowerShell-Engine, die aufgerufen wird, während die Runspace vorhanden ist.

## <a name="module-session-state"></a>Modulsitzungsstatus

Sitzungsstatus des Moduls werden erstellt, wenn das Modul oder eines seiner geschachtelten Module in die Sitzung importiert wird. Wenn ein Modul ein Element wie ein Cmdlet, Funktion oder Skript exportiert, wird ein Verweis auf dieses Element den globalen Sitzungsstatus der Sitzung hinzugefügt. Wenn das Element ausgeführt wird, wird es jedoch in den Sitzungsstatus des Moduls ausgeführt.

## <a name="session-state-data"></a>Sitzungszustandsdaten

Sitzungszustandsdaten können öffentlich oder privat sein. Öffentliche Daten ist für Aufrufe von außerhalb der Sitzungszustand verfügbar, während private Daten nur auf Aufrufe von innerhalb der Sitzungsstatus zur Verfügung steht. Ein Modul kann z. B. eine private Funktion, die nur durch das Modul oder nur intern aufgerufen werden, enthält ein öffentlich-Element, die exportiert wurde. Dies ist ähnlich wie die öffentlichen und privaten Member von .NET Framework-Typ.

Sitzungszustandsdaten werden von der aktuellen Instanz von der ausführungs-Engine innerhalb des Kontexts der aktuellen Windows PowerShell-Sitzung gespeichert. Sitzungszustandsdaten besteht aus den folgenden Elementen:

- Informationen über Pfade

- Informationen zum Laufwerk

- Windows PowerShell-Anbieterinformationen

- Informationen zu den importierten Module und die Verweise auf die Modul-Elemente (z. B. Cmdlets, Funktionen und Skripts), die vom Modul exportiert werden. Diese Informationen und diese Verweise sind für nur den globalen Sitzungsstatus.

- Variablen der Sitzungszustandsinformationen

## <a name="accessing-session-state-data-within-cmdlets"></a>Zugriff auf Sitzungszustandsdaten in Cmdlets

Cmdlets können Zugriff auf Sitzungszustandsdaten entweder indirekt über die [System.Management.Automation.PSCmdlet.Sessionstate*](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState) Eigenschaft, die von der Cmdlet-Klasse oder direkt über die [ System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) Klasse. Die [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) Klasse enthält Eigenschaften, die verwendet werden können, um verschiedene Arten von Sitzungszustandsdaten zu untersuchen.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.PSCmdlet.Sessionstate](/dotnet/api/System.Management.Automation.PSCmdlet.SessionState)

[System.Management.Automation.Sessionstate?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.SessionState)

[Windows PowerShell-Cmdlets](./cmdlet-overview.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
