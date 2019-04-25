---
title: Allgemeine Parameternamen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068426"
---
# <a name="common-parameter-names"></a>Allgemeine Parameternamen

Die in diesem Thema beschriebenen Parameter werden als bezeichnet *allgemeine Parameter*. Diese Cmdlets hinzugefügt werden, indem die Windows PowerShell-Laufzeit und können nicht vom Cmdlet deklariert werden.

> [!NOTE]
> Diese Parameter werden ebenfalls hinzugefügt, um Anbieter-Cmdlets und Funktionen, die mit ergänzt werden die `CmdletBinding` Attribut.

## <a name="general-common-parameters"></a>Allgemeine allgemeine Parameter

Die folgenden Parameter werden für alle Cmdlets hinzugefügt, und es können zugegriffen werden, wenn das Cmdlet ausgeführt wird. Diese Parameter werden von definiert die [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) Klasse.

### <a name="debug-alias-db"></a>Debuggen (Alias: Db)

Datentyp: SwitchParameter

Dieser Parameter gibt an, ob das auf Programmiererebene zu debuggen, die Nachrichten in der Befehlszeile angezeigt werden kann. Diese Nachrichten sind für die Problembehandlung für die Funktionsfähigkeit des Cmdlets vorgesehen und werden durch Aufrufe von generiert die [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) Methode. Debugmeldungen müssen nicht lokalisiert werden soll.

### <a name="erroraction-alias-ea"></a>ErrorAction (Alias: Enterprise Agreement)

Datentyp: Enumeration

Dieser Parameter gibt an, welche Aktion stattfinden soll, wenn ein Fehler auftritt. Die möglichen Werte für diesen Parameter werden von definiert die [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) Enumeration.

### <a name="errorvariable-alias-ev"></a>ErrorVariable (Alias: ev)

Datentyp: Zeichenfolge

Dieser Parameter gibt die Variable in der Objekte platziert werden soll, wenn ein Fehler auftritt. Verwenden Sie zum Anfügen dieser Variablen +*Varname* anstatt durch das Löschen und die Variable festlegen.

### <a name="outvariable-alias-ov"></a>OutVariable (Alias: Ov)

Datentyp: Zeichenfolge

Dieser Parameter gibt die Variable, in der alle Objekte, die vom Cmdlet generiertes auszugeben. Verwenden Sie zum Anfügen dieser Variablen +*Varname* anstatt durch das Löschen und die Variable festlegen.

### <a name="outbuffer-alias-ob"></a>OutBuffer (Alias: Ob)

Datentyp: Int32

Dieser Parameter definiert die Anzahl von Objekten, die in den Ausgabepuffer zu speichern, bevor alle Objekte über die Pipeline übergeben werden. Standardmäßig werden Objekte sofort über die Pipeline übergeben.

### <a name="verbose-alias-vb"></a>Verbose (Alias: Vb)

Datentyp: SwitchParameter

Dieser Parameter gibt an, ob das Cmdlet erläuternde Nachrichten schreibt, die in der Befehlszeile angezeigt werden können. Diese Nachrichten sollen zusätzliche Hilfe für den Benutzer zu ermöglichen, und werden durch Aufrufe der [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) Methode.

### <a name="warningaction-alias-wa"></a>WarningAction (Alias: wa)

Datentyp: Enumeration

Dieser Parameter gibt an, welche Aktion stattfinden soll, wenn das Cmdlet eine Warnmeldung schreibt. Die möglichen Werte für diesen Parameter werden von definiert die [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) Enumeration.

### <a name="warningvariable-alias-wv"></a>WarningVariable (Alias: wv)

Datentyp: Zeichenfolge

Dieser Parameter gibt die Variable, die in der Warnmeldungen gespeichert werden können. Verwenden Sie zum Anfügen dieser Variablen +*Varname* anstatt durch das Löschen und die Variable festlegen.

## <a name="risk-mitigation-parameters"></a>Risikominderung Parameter

Die folgenden Parameter werden Cmdlets hinzugefügt, die Bestätigung anfordert, bevor sie ihre Aktion ausführen. Weitere Informationen zu Anforderungen, die Bestätigung finden Sie unter [Bestätigung anfordern](./requesting-confirmation-from-cmdlets.md). Diese Parameter werden von definiert die [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) Klasse.

### <a name="confirm-alias-cf"></a>Vergewissern Sie sich (Alias: Cf)

Datentyp: SwitchParameter

Dieser Parameter gibt an, ob das-Cmdlet wird eine Meldung, die fragt angezeigt, ob der Benutzer sicher ist, möchten sie fortfahren.

### <a name="whatif-alias-wi"></a>"WhatIf" (Alias: WLAN)

Datentyp: SwitchParameter

Dieser Parameter gibt an, ob das Cmdlet eine Meldung, die beschreibt, die Auswirkungen schreibt der Ausführung des Cmdlets ohne eine Aktion ausführen.

## <a name="transaction-parameters"></a>Transaction-Parameter

Cmdlets, die Transaktionen unterstützen, wird der folgende Parameter hinzugefügt. Diese Parameter werden von definiert die [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) Klasse.

### <a name="usetransaction-alias-usetx"></a>UseTransaction (Alias: Usetx)

Datentyp: SwitchParameter

Dieser Parameter gibt an, ob das-Cmdlet zum Ausführen der Aktion durch die aktuelle Transaktion verwendet.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
