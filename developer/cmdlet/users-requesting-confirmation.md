---
title: Benutzern, die Bestätigung anfordern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067217"
---
# <a name="users-requesting-confirmation"></a>Anfordern der Bestätigung von Benutzern

Wenn Sie den Wert angeben `true` für die `SupportsShouldProcess` der Deklaration der Cmdlet-Attribut angeben, der Benutzer können die `Confirm` Parameter an der Eingabeaufforderung.

In der standardumgebung, Benutzer können angeben, die `Confirm` Parameter oder `"-Confirm:$true` , damit eine Bestätigung angefordert wird bei der [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode wird aufgerufen. Dadurch wird der [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Bestätigung Benutzeranfragen, sogar mit schwerwiegenden Auswirkungen.

Wenn `Confirm` nicht angegeben ist, die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Aufruf fordert die Bestätigung, wenn die `$ConfirmPreference` Einstellungsvariable ist größer als oder gleich der `ConfirmImpact` festlegen, der die -Cmdlet oder Anbieter. Die Standardeinstellung von `$ConfirmPreference` hoch. Aus diesem Grund Bestätigung der Anfrage in der standardumgebung nur Cmdlets und Anbieter, die eine Aktion mit schwerwiegenden Auswirkungen festlegen.

Wenn `Confirm` ist "false" oder, wenn `"-Confirm:$false` angegeben wird, die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Aufruf fordert eine Bestätigung vom Benutzer, und die `$ConfirmPreference` Shellvariable wird ignoriert.

## <a name="remarks"></a>Hinweise

- Für Cmdlets und Anbieter, die angeben, `SupportsShouldProcess`, aber nicht `ConfirmImpact`, diese Aktionen wie "mittleren Impact" Aktionen verarbeitet werden und sie werden nicht standardmäßig aufgefordert. Ihre Impact-Level ist kleiner als die Standardeinstellung für die `$ConfirmPreference` Einstellungsvariable.

- Wenn der Benutzer gibt die `Verbose` -Parameter werden des Vorgangs benachrichtigt werden, auch wenn sie nicht zur Bestätigung aufgefordert werden.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
