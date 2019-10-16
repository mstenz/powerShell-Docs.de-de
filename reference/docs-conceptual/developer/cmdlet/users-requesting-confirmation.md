---
title: Benutzer, die eine Bestätigung anfordern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369249"
---
# <a name="users-requesting-confirmation"></a>Anfordern der Bestätigung von Benutzern

Wenn Sie für den `SupportsShouldProcess`-Parameter der Cmdlet-Attribut Deklaration den Wert `true` angeben, können Benutzer den `Confirm`-Parameter an der Eingabeaufforderung angeben.

In der Standardumgebung können Benutzer den `Confirm`-Parameter oder `"-Confirm:$true` angeben, damit die Bestätigung angefordert wird, wenn die [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode aufgerufen wird. Dies umgeht [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Bestätigungs Anforderungen, auch für Vorgänge mit hohen Auswirkungen.

Wenn `Confirm` nicht angegeben wird, fordert der [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Befehl eine Bestätigung an, wenn die `$ConfirmPreference`-Einstellungs Variable größer oder gleich der `ConfirmImpact`-Einstellung des Cmdlets oder Anbieters ist. Die Standardeinstellung `$ConfirmPreference` ist hoch. In der Standardumgebung gibt es daher nur Cmdlets und Anbieter, die eine Bestätigungs-Aktions Anforderungs Bestätigung angeben.

Wenn `Confirm` false ist oder `"-Confirm:$false` angegeben ist, fordert der [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Befehl eine Bestätigung vom Benutzer an, und die `$ConfirmPreference`-Shellvariable wird ignoriert.

## <a name="remarks"></a>Hinweise

- Für Cmdlets und Anbieter, die `SupportsShouldProcess` angeben, jedoch nicht `ConfirmImpact`, werden diese Aktionen als "mittlere Auswirkung"-Aktionen behandelt, und Sie werden nicht standardmäßig aufgefordert. Die Auswirkungs Stufe ist kleiner als die Standardeinstellung der `$ConfirmPreference`-Einstellungs Variablen.

- Wenn der Benutzer den `Verbose`-Parameter angibt, wird er über den Vorgang benachrichtigt, auch wenn er nicht zur Bestätigung aufgefordert wird.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
