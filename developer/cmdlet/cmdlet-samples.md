---
title: Cmdlet-Beispiele | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b99d53fc-0af9-426b-82ce-09955e031d4b
caps.latest.revision: 13
ms.openlocfilehash: 0fa4a5f804586c51ae6a36121f9aab041b0989cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068449"
---
# <a name="cmdlet-samples"></a>Cmdlet-Beispiele

In diesem Abschnitt wird beschrieben, Beispielcode, der in der Windows PowerShell 2.0 SDK bereitgestellt wird. Sie können Code in den Themen in diesem Abschnitt kopieren, oder öffnen Sie die Quelldateien, die mit dem SDK installiert. Die [Windows PowerShell 2.0 Software Development Kit (SDK)](https://www.microsoft.com/en-us/download/details.aspx?id=2560) bietet ReadMe-Dateien, Quelldateien und Visual Studio-Projektdateien für jedes Beispiel. Mit dem SDK installiert ist, finden Sie die Beispiele unter der `<Drive>:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\` Ordner.

## <a name="in-this-section"></a>In diesem Abschnitt

[GetProcessSample01-Beispiel](./getprocesssample01-sample.md) diesem Beispiel wird gezeigt, wie Sie ein Cmdlet schreiben, die die Prozesse auf dem lokalen Computer abruft.

[GetProcessSample02-Beispiel](./getprocesssample02-sample.md) diesem Beispiel wird gezeigt, wie Sie ein Cmdlet schreiben, die die Prozesse auf dem lokalen Computer abruft. Es bietet einen Namensparameter, der verwendet werden kann, an die Prozesse abgerufen werden sollen.

[Beispiel mit GetProcessSample03](./getprocesssample03-sample.md) diesem Beispiel wird gezeigt, wie Sie ein Cmdlet schreiben, die die Prozesse auf dem lokalen Computer abruft. Es bietet einen Name-Parameter, der ein Objekt aus der Pipeline oder einen Wert aus einer Eigenschaft eines Objekts, dessen Eigenschaftenname den Namen des Parameters entspricht, akzeptieren kann.

[Beispiel für GetProcessSample04](./getprocesssample04-sample.md) diesem Beispiel wird gezeigt, wie Sie ein Cmdlet schreiben, die die Prozesse auf dem lokalen Computer abruft. Es generiert einen Fehler ohne Abbruch, wenn es sich bei Auftreten eines Fehlers beim Abrufen von einem Prozess.

[Beispiel für GetProcessSample05](./getprocesssample05-sample.md) dieses Beispiel zeigt eine vollständige Version des mit dem Get-Proc-Cmdlet.

[StopProcessSample01 Beispiel](./stopprocesssample01-sample.md) in diesem Beispiel wird gezeigt, wie ein Cmdlet schreiben, die fordert Feedback vom Benutzer, bevor sie versucht, einen Prozess zu beenden und zum Implementieren einer `PassThru` Parameter, der angibt, dass der Benutzer möchte, dass das Cmdlet zurückgegeben ein -Objekt.

[Beispiel für StopProcessSample02](./stopprocesssample02-sample.md) diesem Beispiel wird gezeigt, wie Sie ein Cmdlet schreiben, die schreibt, verbose, Debug und Warnmeldungen beim Beenden von Prozessen auf dem lokalen Computer.

[StopProcessSample03 Beispiel](./stopprocesssample03-sample.md) diesem Beispiel wird gezeigt, wie Sie ein Cmdlet schreiben, deren Parameter, Aliase und die aufweisen, Unterstützung von Platzhalterzeichen enthalten.

[Beispiel für StopProcessSample04](./stopprocesssample04-sample.md) dieses Beispiel zeigt, wie zum Schreiben eines Cmdlets, die deklariert Parameter legt fest, gibt an, die Standardparameter festgelegt, und ein Eingabeobjekt akzeptieren.

[Beispiel für Events01](./events01-sample.md) diesem Beispiel wird gezeigt, wie Sie ein Cmdlet zu erstellen, die den Benutzer zum Registrieren von ausgelösten Ereignisse ermöglicht [System.IO.Filesystemwatcher](/dotnet/api/System.IO.FileSystemWatcher). Mit diesem Cmdlet können Benutzer z. B. registrieren eine Aktion, die ausgeführt werden, wenn eine Datei unter einem bestimmten Verzeichnis erstellt wird. In diesem Beispiel leitet sich von der [Microsoft.PowerShell.Commands.Objecteventregistrationbase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) Basisklasse.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
