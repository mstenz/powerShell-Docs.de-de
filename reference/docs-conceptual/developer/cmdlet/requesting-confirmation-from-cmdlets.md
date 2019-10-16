---
title: Anfordern der Bestätigung von Cmdlets | Microsoft-Dokumentation
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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369529"
---
# <a name="requesting-confirmation-from-cmdlets"></a>Anfordern der Bestätigung von Cmdlets

Cmdlets sollten eine Bestätigung anfordern, wenn Sie im Begriff sind, Änderungen am System vorzunehmen, das sich außerhalb der Windows PowerShell-Umgebung befindet. Wenn ein Cmdlet z. b. das Hinzufügen eines Benutzerkontos oder das Abbrechen eines Prozesses durchführt, sollte das Cmdlet eine Bestätigung des Benutzers erfordern, bevor es fortgesetzt wird. Wenn im Gegensatz dazu ein Cmdlet eine Windows PowerShell-Variable ändern soll, muss das Cmdlet keine Bestätigung erfordern.

Um eine Bestätigungs Anforderung zu stellen, muss das Cmdlet angeben, dass Bestätigungs Anforderungen unterstützt werden. Außerdem muss das Cmdlet " [System. Management. Automation. Cmdlet. Schulter dprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " und " [System. Management. Automation. Cmdlet" aufgerufen werden. ](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)(optional) Methoden zum Anzeigen einer Bestätigungs Anforderungs Nachricht.

## <a name="supporting-confirmation-requests"></a>Unterstützen von Bestätigungs Anforderungen

Zur Unterstützung von Bestätigungs Anforderungen muss das Cmdlet den `SupportsShouldProcess`-Parameter des Cmdlet-Attributs auf `true` festlegen. Dies ermöglicht die Cmdlet-Parameter "`Confirm`" und "`WhatIf`", die von Windows PowerShell bereitgestellt werden. Mit dem Parameter "`Confirm`" kann der Benutzer steuern, ob die Bestätigungs Anforderung angezeigt wird. Mit dem Parameter "`WhatIf`" kann der Benutzer bestimmen, ob das Cmdlet eine Meldung anzeigen oder seine Aktion ausführen soll. Fügen Sie die Parameter "`Confirm`" und "`WhatIf`" nicht manuell zu einem Cmdlet hinzu.

Das folgende Beispiel zeigt eine Cmdlet-Attribut Deklaration, die Bestätigungs Anforderungen unterstützt.

```csharp
[Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
        SupportsShouldProcess = true)]
```

## <a name="calling-the-confirmation-request-methods"></a>Aufrufen der Bestätigungs Anforderungs Methoden

Geben Sie im Cmdlet-Code die [System. Management. Automation. Cmdlet. schuldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode vor dem Vorgang an, durch den das System geändert wird. Entwerfen Sie das Cmdlet so, dass der Vorgang, wenn der-Rückruf den Wert `false` zurückgibt, nicht ausgeführt wird und das Cmdlet den nächsten Vorgang verarbeitet.

## <a name="calling-the-shouldcontinue-method"></a>Aufrufen der Methode "schuldcontinue"

Die meisten Cmdlets fordern eine Bestätigung nur mithilfe der [System. Management. Automation. Cmdlet. schuldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode an. In einigen Fällen ist jedoch möglicherweise eine zusätzliche Bestätigung erforderlich. Ergänzen Sie in diesen Fällen den " [System. Management. Automation. Cmdlet. Schulter dprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) "-Befehl durch einen Rückruf der [System. Management. Automation. Cmdlet. Schulter dcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode. Dadurch kann das Cmdlet oder der Anbieter den Gültigkeitsbereich der ja-Antwort auf die **gesamte** Antwort der Bestätigungsaufforderung besser steuern.

Wenn ein Cmdlet die [System. Management. Automation. Cmdlet. tiondcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode aufruft, muss das Cmdlet auch einen `Force`-Schalter Parameter bereitstellen. Wenn der Benutzer `Force` angibt, wenn der Benutzer das Cmdlet aufruft, sollte das Cmdlet weiterhin [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)aufrufen, aber es sollte den Aufruf von [System. Management. Automation. Cmdlet. undcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)umgehen.

[System. Management. Automation. Cmdlet. tiondcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) löst eine Ausnahme aus, wenn Sie von einer nicht interaktiven Umgebung aufgerufen wird, in der der Benutzer nicht dazu aufgefordert werden kann. Durch das Hinzufügen eines `Force`-Parameters wird sichergestellt, dass der Befehl immer noch ausgeführt werden kann, wenn er in einer nicht interaktiven Umgebung aufgerufen wird.

Im folgenden Beispiel wird gezeigt, wie " [System. Management. Automation. Cmdlet. Schulter dprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " und " [System. Management. Automation. Cmdlet. daudcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)" aufgerufen werden.

```csharp
if (ShouldProcess (...) )
{
  if (Force || ShouldContinue(...))
  {
     // Add code that performs the operation.
  }
}
```

Abhängig von der Umgebung, in der das Cmdlet aufgerufen wird, kann das Verhalten eines " [System. Management. Automation. Cmdlet. daudprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) "-Aufrufes variieren. Mithilfe der vorherigen Richtlinien wird sichergestellt, dass sich das Cmdlet unabhängig von der Host Umgebung konsistent mit anderen Cmdlets verhält.

Ein Beispiel für den Aufruf der [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode finden [Sie unter Anfordern von Bestätigungen](./how-to-request-confirmations.md).

## <a name="specify-the-impact-level"></a>Festlegen der Auswirkungs Stufe

Wenn Sie das Cmdlet erstellen, geben Sie die Auswirkungs Stufe (Schweregrad) der Änderung an. Legen Sie zu diesem Zweck den Wert des Parameters "`ConfirmImpact`" des Cmdlet-Attributs auf "hoch", "Mittel" oder "niedrig" fest. Sie können nur dann einen Wert für `ConfirmImpact` angeben, wenn Sie auch den Parameter "`SupportsShouldProcess`" für das Cmdlet angeben.

Bei den meisten Cmdlets müssen Sie `ConfirmImpact` nicht explizit angeben.  Verwenden Sie stattdessen die Standardeinstellung des-Parameters, der Mittel ist. Wenn Sie `ConfirmImpact` auf High festlegen, wird der Vorgang standardmäßig bestätigt. Reservieren Sie diese Einstellung für hochgradig unterbrechungsfreie Aktionen, z. b. das Neuformatieren eines Festplatten Laufwerks.

## <a name="calling-non-confirmation-methods"></a>Aufrufen von nicht-Bestätigungs Methoden

Wenn das Cmdlet oder der Anbieter eine Nachricht senden, aber keine Bestätigung anfordern muss, können die folgenden drei Methoden aufgerufen werden. Vermeiden Sie die Verwendung der [System. Management. Automation. Cmdlet. Write Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Methode zum Senden von Nachrichten dieser Typen, da die [System. Management. Automation. Cmdlet. Write Object](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) -Ausgabe mit der normalen Ausgabe des Cmdlets oder Anbieters intermischt. , wodurch das Schreiben von Skripts schwierig wird.

- Um den Benutzer zu warnen und den Vorgang fortzusetzen, kann das Cmdlet oder der Anbieter die [System. Management. Automation. Cmdlet. Write Warning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning) -Methode aufrufen.

- Um zusätzliche Informationen bereitzustellen, die der Benutzer mithilfe des Parameters `Verbose` abrufen kann, kann das Cmdlet oder der Anbieter die [System. Management. Automation. Cmdlet. Write-Verbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) -Methode aufrufen.

- Zum Bereitstellen von Details auf Debugebene für andere Entwickler oder für den Produktsupport kann das Cmdlet oder der Anbieter die [System. Management. Automation. Cmdlet. Write Team Debug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) -Methode abrufen. Der Benutzer kann diese Informationen mithilfe des Parameters "`Debug`" abrufen.

Cmdlets und Anbieter wenden zuerst die folgenden Methoden an, um eine Bestätigung anzufordern, bevor Sie versuchen, einen Vorgang auszuführen, der ein System außerhalb von Windows PowerShell ändert:

- [System. Management. Automation. Cmdlet. schuldprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess)

- [System. Management. Automation. Provider. cmdletprovider. schuldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess)

Dies erfolgt durch Aufrufen der [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode, die den Benutzer auffordert, den Vorgang zu bestätigen, je nachdem, wie der Benutzer den Befehl aufgerufen hat.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
