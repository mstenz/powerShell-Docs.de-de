---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Verwenden der Windows PowerShell 2.0 Engine
ms.openlocfilehash: e00fb71c7fc32f5b48bc17ef5b25f910a846c893
ms.sourcegitcommit: 1748b2bdfae81d98097962c6c25c25df4bced1d8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2020
ms.locfileid: "84262612"
---
# <a name="using-the-windows-powershell-20-engine"></a>Verwenden der Windows PowerShell 2.0 Engine

Windows PowerShell darauf ausgelegt, mit früheren Versionen abwärtskompatibel zu sein. Cmdlets, Anbieter, Snap-Ins, Module und Skripts, die für Windows PowerShell 2.0 geschrieben wurden, können unverändert in neueren Versionen von Windows PowerShell ausgeführt werden. In Microsoft .NET Framework 4 wurde jedoch die Richtlinie für die Laufzeitaktivierung geändert.
Windows PowerShell-Hostprogramme, die für Windows PowerShell 2.0 geschrieben und mit Common Language Runtime (CLR) 2.0 kompiliert wurden, können nicht unverändert in neuen Versionen von Windows PowerShell ausgeführt werden, die mit CLR 4.0 (oder höher) kompiliert wurden.

Die Windows PowerShell 2.0 Engine sollte nur verwendet werden, wenn ein vorhandenes Skript oder Hostprogramm nicht ausgeführt werden kann, da es inkompatibel mit Windows PowerShell 5.1 ist. Beispiele hierfür sind ältere Versionen von Exchange oder SQL Server-Modulen. Solche Fälle sind allerdings eher selten.

Viele Programme, die Windows PowerShell 2.0 Engine benötigen, starten sie automatisch. Diese Anweisungen gelten für die seltenen Fälle, in denen Sie die Engine manuell starten müssen.

## <a name="deprecation-and-security-concerns"></a>Eingestellte Unterstützung und Sicherheitsaspekte

Windows PowerShell 2.0 wurde im August 2017 eingestellt. Weitere Informationen finden Sie in der [Ankündigung][] im PowerShell-Blog.

In Windows PowerShell 2.0 fehlt eine beträchtliche Menge der Härtungs- und Sicherheitsfeatures, die in den Versionen 3, 4 und 5 hinzugefügt wurden. Es wird dringend empfohlen, dass Benutzer diese Version nicht verwenden, wenn dies möglich ist. Weitere Informationen finden Sie unter [Ein Vergleich der Sicherheit von Shell- und Skriptsprachen][] und [PowerShell ♥ The Blue Team][blueteam].

## <a name="installing-and-enabling-required-programs"></a>Installieren und Aktivieren erforderlicher Programme

Aktivieren Sie Windows PowerShell 2.0 Engine und Microsoft .NET Framework 3.5 mit Service Pack 1, bevor Sie Windows PowerShell 2.0 Engine starten. Anweisungen hierzu finden Sie unter [Installieren von Windows PowerShell][].

Systeme, auf denen Windows Management Framework 3.0 oder höher installiert ist, verfügen über alle erforderlichen Komponenten. Es ist keine weitere Konfiguration erforderlich. Informationen zum Installieren von Windows Management Framework finden Sie unter [Installieren und Konfigurieren von WMF][].

## <a name="how-to-start-the-windows-powershell-20-engine"></a>So starten Sie Windows PowerShell 2.0 Engine

Beim Starten von Windows PowerShell wird die neueste Version standardmäßig gestartet. Verwenden Sie den „Version“-Parameter von `PowerShell.exe`, um Windows PowerShell mit Windows PowerShell 2.0 Engine zu starten. Sie können den Befehl an jeder Eingabeaufforderung einschließlich Windows PowerShell und „Cmd.exe“ ausführen.

```
PowerShell.exe -Version 2
```

## <a name="how-to-start-a-remote-session-with-the-windows-powershell-20-engine"></a>So starten Sie eine Remotesitzung mit Windows PowerShell 2.0 Engine

Erstellen Sie auf dem Remotecomputer eine Sitzungskonfiguration (auch _Endpunkt_ genannt), die Windows PowerShell 2.0 Engine lädt, um Windows PowerShell 2.0 Engine in einer Remotesitzung auszuführen. Die Sitzungskonfiguration wird auf dem Remotecomputer gespeichert und kann von jedem autorisierten Benutzer verwendet werden, um Sitzungen zu erstellen, die Windows PowerShell 2.0 Engine verwenden.

Dies ist eine komplexe Aufgabe, die in der Regel von einem Systemadministrator ausgeführt wird.

Im folgenden Verfahren wird der **PSVersion**-Parameter des Cmdlets [Register-PSSessionConfiguration][] zum Erstellen einer Sitzungskonfiguration verwendet, die Windows PowerShell 2.0 Engine nutzt. Sie können auch den **PowerShellVersion**-Parameter des Cmdlets [New-PSSessionConfigurationFile][] verwenden, um eine Sitzungskonfigurationsdatei für eine Sitzung zu erstellen, die Windows PowerShell 2.0 Engine lädt. Sie können auch den **PSVersion**-Parameter des Parameters [Set-PSSessionConfiguration][] verwenden, um eine Sitzungskonfiguration so zu ändern, dass Windows PowerShell 2.0 Engine verwendet wird.

Weitere Informationen zu Sitzungskonfigurationsdateien finden Sie unter [about_Session_Configuration_Files][].
Informationen zu Sitzungskonfigurationen, einschließlich Einrichtung und Sicherheit, finden Sie unter [about_Session_Configurations][].

### <a name="to-start-a-remote-windows-powershell-20-session"></a>Gehen Sie folgendermaßen vor, um eine Remotesitzung von Windows PowerShell 2.0 zu starten

1. Verwenden Sie den **PSVersion**-Parameter des Cmdlets `Register-PSSessionConfiguration` mit dem Wert `2.0`, um eine Sitzungskonfiguration zu erstellen, die Windows PowerShell 2.0 Engine erfordert.
   Führen Sie diesen Befehl auf dem Computer auf der Serverseite oder dem empfangenden Ende der Verbindung aus.

   Der folgende Befehl erstellt die PS2-Sitzungskonfiguration auf dem Computer „Server01“. Starten Sie Windows PowerShell mit der Option **Als Administrator ausführen**, um diesen Befehl auszuführen.

   ```powershell
   Register-PSSessionConfiguration -Name PS2 -PSVersion 2.0
   ```

1. Zum Erstellen einer Sitzung auf dem Computer „Server01“, der die PS2-Sitzungskonfiguration nutzt, verwenden Sie den **ConfigurationName**-Parameter von Cmdlets, die eine Remotesitzung aufbauen, wie z. B. das Cmdlet „New-PSSession“.

   Wenn eine Sitzung gestartet wird, die die Sitzungskonfiguration verwendet, wird Windows PowerShell 2.0 Engine automatisch in die Sitzung geladen.

   Der folgende Befehl erstellt eine Sitzung auf dem Computer „Server01“, die die PS2-Sitzungskonfiguration verwendet. Der Befehl speichert die Sitzung in der Variablen `$s`.

   ```powershell
   $s = New-PSSession -ComputerName Server01 -ConfigurationName PS2
   ```

## <a name="how-to-start-a-background-job-with-the-windows-powershell-20-engine"></a>So starten Sie einen Hintergrundauftrags mit Windows PowerShell 2.0 Engine

Verwenden Sie den **PSVersion**-Parameter des Cmdlets [Start-Job][] zum Starten eines Hintergrundauftrags mit Windows PowerShell 2.0 Engine.

Der folgende Befehl startet einen Hintergrundauftrag mit Windows PowerShell 2.0 Engine

```powershell
Start-Job {Get-Process} -PSVersion 2.0
```

Weitere Informationen zu Hintergrundaufträgen finden Sie unter [about_Jobs][].

<!-- link references -->
[Ankündigung]: https://devblogs.microsoft.com/powershell/windows-powershell-2-0-deprecation/
[Ein Vergleich der Sicherheit von Shell- und Skriptsprachen]: https://devblogs.microsoft.com/powershell/a-comparison-of-shell-and-scripting-language-security/
[blueteam]: https://devblogs.microsoft.com/powershell/powershell-the-blue-team/
[Installieren von Windows PowerShell]: install/Installing-Windows-PowerShell.md
[Installieren und Konfigurieren von WMF]: wmf/setup/install-configure.md
[Register-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Register-PSSessionConfiguration
[New-PSSessionConfigurationFile]: /powershell/module/Microsoft.PowerShell.Core/New-PSSessionConfiguration
[Set-PSSessionConfiguration]: /powershell/module/Microsoft.PowerShell.Core/Set-PSSessionConfiguration
[about_Session_Configuration_Files]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configuration_Files
[about_Session_Configurations]: /powershell/module/Microsoft.PowerShell.Core/about/about_Session_Configurations
[Start-Job]: /powershell/module/microsoft.powershell.core/start-job
[about_Jobs]: /powershell/module/microsoft.powershell.core/about/about_jobs
