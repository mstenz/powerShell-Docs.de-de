---
title: Bestätigung von-Cmdlets anfordern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConfirmImpact [PowerShell Programmer's Guide], described
- ShouldContinue [PowerShell Programmer's Guide], described
- user feedback [PowerShell Programmer's Guide], requesting
- ShouldProcess [PowerShell Programmer's Guide], described
- ConfirmPreference [PowerShell Programmer's Guide], described
ms.assetid: 37d6e87f-57b7-40bd-b645-392cf0b6e88e
caps.latest.revision: 13
ms.openlocfilehash: 0c0517ef7fbd5ae6434773a2dfe276f3a8c35f39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067483"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Anfordern der Bestätigung von Cmdlets

Cmdlets sollten Bestätigung anfordern, wenn sie sind im Begriff, eine Änderung am System vornehmen, die außerhalb der Windows PowerShell-Umgebung ist. Beispielsweise ist ein Cmdlet zum Hinzufügen eines Benutzerkontos oder einen Prozess beenden, sollte das Cmdlet erfordern, Bestätigung durch den Benutzer, bevor sie fortgesetzt wird. Im Gegensatz dazu ist ein Cmdlet zu eine Windows PowerShell-Variablen zu ändern, muss das Cmdlet nicht eine Bestätigung erforderlich ist.

Um Bestätigung anfordern, das Cmdlet angeben muss, dass sie die Bestätigungs-Anforderungen unterstützt, und aufgerufen werden muss die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) (optional) Methoden zum Anzeigen einer Bestätigung-Request-Nachricht.

## <a name="supporting-confirmation-requests"></a>Anforderungen für unterstützende Bestätigung

Um Bestätigung Anforderungen zu unterstützen, muss das-Cmdlet Festlegen der `SupportsShouldProcess` Parameter des Attributs, das Cmdlet `true`. Dies ermöglicht die `Confirm` und `WhatIf` Cmdlet-Parameter, die von Windows PowerShell bereitgestellt werden. Die `Confirm` Parameter ermöglicht den Benutzer die Steuerung, ob die Anforderung zur Bestätigung angezeigt wird. Die `WhatIf` Parameter ermöglicht dem Benutzer, zu bestimmen, ob das Cmdlet eine Meldung angezeigt, oder die Aktion durchgeführt werden soll. Fügen Sie nicht manuell hinzu der `Confirm` und `WhatIf` Parameter an ein Cmdlet.

Das folgende Beispiel zeigt die Deklaration eines Cmdlet-Attributs, das Bestätigung-Anforderungen unterstützt.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Aufrufen der Methoden der Bestätigung-Anforderung

Rufen Sie in der Cmdlet-Code, der [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode auf, bevor der Vorgang, der ändert das System ausgeführt wird. Das Cmdlet so konzipieren, dass, auch wenn der Aufruf der Wert zurückgegeben `false`, der Vorgang nicht ausgeführt wird und das-Cmdlet verarbeitet den nächsten Vorgang.

## <a name="calling-the-shouldcontinue-method"></a>Aufrufen der Methode "shouldcontinue"

Die meisten Cmdlets Anforderung nur mit der Bestätigung der [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode. Manchmal erfordert jedoch möglicherweise zusätzliche Bestätigung. In diesen Fällen ergänzen die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Aufrufen durch einen Aufruf der [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode. Dies ermöglicht das Cmdlet oder den Anbieter, um den Umfang der genauere steuern die **Ja, alle** als Antwort auf die bestätigungsaufforderung.

Wenn ein Cmdlet Ruft die [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode, mit dem Cmdlet muss auch angeben einer `Force` switch-Parameter. Wenn der Benutzer gibt `Force` , wenn der Benutzer das-Cmdlet aufgerufen wird, sollten immer noch das-Cmdlet Aufrufen [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess), jedoch sollten sie den Aufruf von umgehen [ System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

[System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) wird eine Ausnahme ausgelöst, wenn sie von einer nicht-interaktive Umgebung aufgerufen wird, in denen der Benutzer kann nicht aufgefordert werden. Hinzufügen einer `Force` Parameter wird sichergestellt, dass der Befehl noch ausgeführt werden kann, wenn sie in einer nicht-interaktive Umgebung aufgerufen wird.

Das folgende Beispiel zeigt das Aufrufen von [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue).

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Das Verhalten einer [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Aufruf kann variieren, abhängig von der Umgebung, in der das-Cmdlet aufgerufen wird. Verwenden die vorherigen Richtlinien helfen sicherzustellen, dass das Cmdlet konsistent mit anderen Cmdlets, unabhängig von der hostumgebung verhält.

Ein Beispiel eines Aufrufs der [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode finden Sie unter [wie Bestätigungen anfordern](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Geben Sie den Schweregrad

Wenn Sie das Cmdlet erstellen, geben Sie den Schweregrad (der Schweregrad), der die Änderung. Legen Sie den Wert der zu diesem Zweck die `ConfirmImpact` Parameter des Cmdlet-Attributs, hoch, Mittel oder niedrig. Sie können angeben, einen Wert für `ConfirmImpact` nur wenn Sie auch angeben, die `SupportsShouldProcess` Parameter für das Cmdlet.

Für die meisten Cmdlets verfügen Sie nicht explizit angeben, über `ConfirmImpact`.  Verwenden Sie stattdessen die Standardeinstellung des Parameters, das Medium ist. Setzen Sie `ConfirmImpact` auf hoch, wird standardmäßig der Vorgang bestätigt werden. Diese Einstellung für hoch Unterbrechungen führen Aktionen, wie z. B. das Neuformatieren eines Volumes für die Festplatte zu reservieren.

## <a name="calling-non-confirmation-methods"></a>Aufrufen von Methoden für nicht-Bestätigung

Wenn das Cmdlet oder der Anbieter muss einer Nachricht senden, aber keine Bestätigung angefordert, können sie die folgenden drei Methoden aufrufen. Vermeiden Sie die Verwendung der [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) Methode zum Senden von Nachrichten dieser Typen da [System.Management.Automation.Cmdlet.WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) Ausgabe vermischt werden mit der normalen Ausgabe des Cmdlets oder der Anbieter erschwert das Skript schreiben.

- Um Vorsicht des Benutzers und den Vorgang fortsetzen, das Cmdlet oder dem Anbieter kann Aufrufen der [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) Methode.

- Um zusätzliche Informationen bereitzustellen, die der Benutzer abrufen können mithilfe der `Verbose` -Parameter, das Cmdlet oder Anbieter erreichen die [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) Methode.

- Um auf Debug-Ebene-Details für andere Entwickler oder für den Produktsupport bereitzustellen, das Cmdlet oder dem Anbieter kann rufen die [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) Methode. Der Benutzer kann abrufen, diese Informationen mithilfe der `Debug` Parameter.

Cmdlets und Anbieter rufen Sie zuerst die folgenden Methoden zum Bestätigung anzufordern, bevor sie versuchen, einen Vorgang auszuführen, der ein System außerhalb der Windows PowerShell ändern:

- [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Zu diesem Zweck das Aufrufen der [System.Management.Automation.Cmdlet.Shouldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode, die der Benutzer aufgefordert, bestätigen den Vorgang, der basierend auf wie der Benutzer den Befehl aufgerufen.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
