---
title: Erste Schritte mit PowerShell
description: Informationen, wo Sie als neuer Benutzer PowerShell finden und wie Sie sie starten können.
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 0f72fb5baf5b829142b18ed774261e9b3b66291b
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438021"
---
# <a name="chapter-1---getting-started-with-powershell"></a>Kapitel 1: Erste Schritte mit PowerShell

Ich stelle häufig fest, dass bei Referenten auf Konferenzen und bei Benutzergruppenbesprechungen PowerShell bereits läuft, wenn sie mit einer Präsentation für Einsteiger beginnen. Dieses Buch beginnt mit dem Beantworten der Fragen, die ich in solchen Sitzungen von Teilnehmern gehört habe, die PowerShell noch nie benutzt hatten.

Dieses Kapitel konzentriert sich insbesondere auf das Auffinden und Starten von PowerShell sowie das Lösen einiger der anfänglichen Probleme, die bei neuen Benutzern von PowerShell auftreten können. Stellen Sie sicher, dass Sie die in diesem Kapitel gezeigten Beispiele auf Ihrem Windows 10-Laborumgebungscomputer durchlaufen und nachvollziehen.

## <a name="what-do-i-need-to-get-started-with-powershell"></a>Was benötige ich für den Einstieg bei PowerShell?

Alle modernen Versionen von Windows-Betriebssystemen werden mit einer vorinstallierten PowerShell ausgeliefert. Wenn Sie eine ältere Version als 5.1 ausführen, sollten Sie die neueste Version installieren.

- Informationen für ein Upgrade auf Windows PowerShell 5.1 finden Sie unter [Aktualisieren einer vorhandenen Windows PowerShell][].
- Informationen zur Installation der neuesten Version von PowerShell finden Sie unter [Installieren von PowerShell][].

## <a name="where-do-i-find-powershell"></a>Wo finde ich PowerShell?

Die einfachste Möglichkeit, um PowerShell unter Windows 10 zu finden, besteht darin, **PowerShell** in die Suchleiste einzugeben, wie in Abbildung 1-1 dargestellt.

![Abbildung 1-1](media/figure1-1.png)

Beachten Sie, dass in Abbildung 1-1 vier verschiedene Tastenkombinationen für PowerShell gezeigt werden. Auf dem Computer, der zu Demonstrationszwecken in diesem Buch verwendet wird, wird die 64-Bit-Version von Windows 10 ausgeführt, weshalb es eine 64-Bit-Version der PowerShell-Konsole und der PowerShell ISE (Integrated Scripting Environment) gibt sowie eine 32-Bit-Version von diesen beiden Komponenten, die durch das Suffix (x86) bei den Tastenkombinationen kenntlich ist. Wenn Sie eine 32-Bit-Version von Windows 10 ausführen, haben Sie nur zwei Tastenkombinationen. Diese Elemente haben nicht das Suffix (x86) und sind 32-Bit-Versionen. Wenn Sie über ein 64-Bit-Betriebssystem verfügen, empfehle ich Ihnen, die 64-Bit-Version von PowerShell auszuführen, es sei denn, Sie haben einen bestimmten Grund für die Ausführung der 32-Bit-Version.

Informationen zum Starten von PowerShell auf anderen Versionen von Windows finden Sie unter [Starten von Windows PowerShell][].

## <a name="how-do-i-launch-powershell"></a>Wie starte ich PowerShell?

In den von mir unterstützten Produktionsumgebungen für Unternehmen verwende ich drei verschiedene Active Directory-Benutzerkonten. Ich benutze eben diese Konten in der in diesem Buch verwendeten Laborumgebung. Ich melde mich bei dem Windows 10-Computer als Domänenbenutzer an, der kein Domänen- oder lokaler Administrator ist.

Ich habe die PowerShell-Konsole durch Klicken auf die Verknüpfung „Windows PowerShell“ gestartet, wie in Abbildung 1-1 dargestellt.

![Abbildung 1-4](media/figure1-4.png)

Beachten Sie, dass in der Titelleiste der PowerShell-Konsole „Windows PowerShell“ steht, wie in Abbildung 1-4 dargestellt. Einige Befehle werden zwar einwandfrei ausgeführt, doch PowerShell kann nicht die Benutzerkontensteuerung (User Access Control, UAC) nutzen. Dies bedeutet, dass es nicht zur Erhöhung der Rechte bei Aufgaben auffordern kann, die die Genehmigung eines Administrators erfordern.
Die folgende Fehlermeldung wird generiert:

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

Die Lösung für dieses Problem besteht darin, PowerShell als Domänenbenutzer auszuführen, der lokaler Administrator ist.
Auf diese Weise ist mein zweites Domänenbenutzerkonto konfiguriert. Bei Verwendung des Prinzips der geringsten Rechte sollte dieses Konto WEDER Domänenadministrator sein NOCH über erhöhte Rechte in der Domäne verfügen.

Schließen Sie PowerShell. Starten Sie die PowerShell-Konsole neu, wobei Sie aber diesmal mit der rechten Maustaste auf die Verknüpfung **Windows PowerShell** klicken, und wählen Sie **Als Administrator ausführen** aus, wie in Abbildung 1-5 dargestellt.

![Abbildung 1-5](media/figure1-5.png)

Wenn Sie als normaler Benutzer bei Windows angemeldet sind, werden Sie zur Eingabe von Anmeldeinformationen aufgefordert. Ich gebe die Anmeldeinformationen für mein Benutzerkonto ein, das Domänenbenutzer und lokaler Administrator ist, wie in Abbildung 1-6 dargestellt.

![Abbildung 1-6](media/figure1-6.png)

Nachdem PowerShell als Administrator neu gestartet wurde, sollte in der Titelleiste „Administrator: Windows PowerShell“ stehen, wie in Abbildung 1-7 dargestellt.

![Abbildung 1-7](media/figure1-7.png)

Nachdem PowerShell nun mit erhöhten Rechten als lokaler Administrator ausgeführt wird, stellt die Benutzerkontensteuerung kein Problem mehr dar, wenn auf dem lokalen Computer ein Befehl ausgeführt wird, der normalerweise eine Aufforderung zur Erhöhung der Rechte erfordern würde. Denken Sie jedoch daran, dass jeder Befehl, der aus dieser PowerShell-Konsoleninstanz mit erhöhten Rechten ausgeführt wird, ebenfalls mit diesen erhöhten Rechten ausgeführt wird.

Um das Auffinden von PowerShell und deren Start als Administrator zu vereinfachen, empfehle ich, sie an die Taskleiste anzuheften und für sie festzulegen, dass Sie bei jeder Ausführung automatisch als Administrator gestartet wird.

Suchen Sie erneut nach PowerShell, klicken Sie nur diesmal mit der rechten Maustaste darauf, und wählen Sie „An Taskleiste anheften“ aus, wie in Abbildung 1-8 dargestellt.

![Abbildung 1-8](media/figure1-8.png)

Klicken Sie mit der rechten Maustaste auf die PowerShell-Verknüpfung, die nun an die Taskleiste angeheftet ist, und wählen Sie „Eigenschaften“ aus, wie in Abbildung 1-9 dargestellt.

![Abbildung 1-9](media/figure1-9.png)

Klicken Sie auf „Erweitert“, wie durch #1 in Abbildung 1-10 markiert, aktivieren Sie dann das Kontrollkästchen „Als Administrator ausführen“, wie durch #2 in Abbildung 1-10 markiert, und klicken Sie dann zweimal auf „OK“, um die Änderungen zu übernehmen und beide Dialogfelder zu schließen.

![Abbildung 1-10](media/figure1-10.png)

Sie müssen sich nun keine Gedanken mehr über das Auffinden von PowerShell zu machen oder darüber, ob sie als Administrator ausgeführt wird oder nicht.

Wenn Sie PowerShell mit erhöhten Rechten als Administrator ausführen, um Probleme mit der Benutzerkontensteuerung zu verhindern, wirkt sich dies nur auf Befehle aus, die auf dem lokalen Computer ausgeführt werden. Es hat keine Auswirkungen auf Befehle, die sich auf Remotecomputer beziehen.

## <a name="what-version-of-powershell-am-i-running"></a>Welche PowerShell-Version führe ich aus?

Es gibt eine Reihe automatischer Variablen in PowerShell, die Zustandsinformationen speichern. Eine dieser Variablen ist `$PSVersionTable`, die eine Hashtabelle enthält, die zum Anzeigen der relevanten PowerShell-Versionsinformationen verwendet werden kann:

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Neuere Versionen von Windows PowerShell werden als Bestandteil des Windows Management Frameworks (WMF) verteilt. In Abhängigkeit von der WMF-Version ist eine bestimmte Version von .NET Framework erforderlich. Informationen für ein Upgrade auf Windows PowerShell 5.1 finden Sie unter [Aktualisieren einer vorhandenen Windows PowerShell][].

## <a name="execution-policy"></a>Ausführungsrichtlinie

Entgegen der gängigen Annahme, stellt die Ausführungsrichtlinie in PowerShell keine Sicherheitsgrenze dar. Sie ist darauf ausgelegt, einen Benutzer daran zu hindern, unwissentlich ein Skript auszuführen. Ein entschlossener Benutzer kann die Ausführungsrichtlinie in PowerShell mühelos umgehen. In Tabelle 1-2 wird die Standardausführungsrichtlinie für die aktuellen Windows-Betriebssysteme angezeigt.

| Windows-Betriebssystemversion | Standardausführungsrichtlinie |
| -------------------------------- | ------------------------ |
| Server 2019                      | Remote signiert            |
| Server 2016                      | Remote signiert            |
| Windows 10                       | Eingeschränkt               |

Unabhängig von der Einstellung der Ausführungsrichtlinie können alle PowerShell-Befehle interaktiv ausgeführt werden. Die Ausführungsrichtlinie gilt nur für Befehle, die in einem Skript ausgeführt werden. Das Cmdlet `Get-ExecutionPolicy` wird verwendet, um zu bestimmen, wie die aktuelle Ausführungsrichtlinieneinstellung lautet, und das Cmdlet `Set-ExecutionPolicy` wird verwendet, um die Ausführungsrichtlinie zu ändern. Meine Empfehlung ist es, die **RemoteSigned**-Richtlinie zu verwenden, die erfordert, dass heruntergeladene Skripts von einem vertrauenswürdigen Herausgeber signiert sind, damit Sie ausgeführt werden können.

Überprüfen Sie die aktuelle Ausführungsrichtlinie:

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

PowerShell-Skripts können gar nicht ausgeführt werden, wenn die Ausführungsrichtlinie auf **Eingeschränkt** festgelegt ist. Dies ist die Standardeinstellung in allen Windows-Clientbetriebssystemen. Um das Problem zu veranschaulichen, speichern Sie den folgenden Code als `.ps1`-Datei namens `Stop-TimeService.ps1`.

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

Dieser Befehl wird interaktiv ohne Fehler ausgeführt, solange PowerShell mit erhöhten Rechten als Administrator ausgeführt wird. Sobald er aber als Skriptdatei gespeichert wird und Sie versuchen, das Skript auszuführen, wird ein Fehler generiert:

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

Beachten Sie, dass der Fehler, der im vorherigen Resultset zu sehen ist, genau angibt, wo das Problem liegt (das Ausführen von Skripts ist auf diesem System deaktiviert). Wenn Sie einen Befehl in PowerShell ausführen, der eine Fehlermeldung generiert, achten Sie darauf, dass Sie die Fehlermeldung lesen, anstatt einfach nur den Befehl erneut auszuführen und zu hoffen, dass er diesmal erfolgreich ausgeführt wird.

Ändern Sie die PowerShell-Ausführungsrichtlinie auf „Remote signiert“.

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

Lesen Sie unbedingt die Warnung, die angezeigt wird, wenn Sie die Ausführungsrichtlinie ändern. Ich empfehle Ihnen außerdem, sich das Hilfethema [about_Execution_Policies][] anzusehen, um sicherzustellen, dass Sie die Sicherheitsimplikationen verstehen, die mit der Änderung der Ausführungsrichtlinie einhergehen.

Nun, da die Ausführungsrichtlinie auf **RemoteSigned** festgelegt ist, wird das Skript `Stop-TimeService.ps1` fehlerfrei ausgeführt.

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

Stellen Sie sicher, dass Sie Ihren Windows-Zeitdienst starten, bevor Sie fortfahren, da sonst unvorhersehbare Probleme auftreten können.

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a>Zusammenfassung

In diesem Kapitel haben Sie erfahren, wie Sie PowerShell finden und starten, und wie Sie eine Verknüpfung erstellen, mit der PowerShell als Administrator gestartet wird. Außerdem haben Sie Informationen über die Standardausführungsrichtlinie erhalten und erfahren, wie man diese ändert.

## <a name="review"></a>Überprüfung

1. Wie bestimmen Sie, welche PowerShell-Version auf einem Computer ausgeführt wird?
1. Warum ist es wichtig, PowerShell mit erhöhten Rechten als Administrator zu starten?
1. Wie bestimmen Sie die aktuelle Ausführungsrichtlinie von PowerShell?
1. Was verhindert die Standardausführungsrichtlinie von PowerShell auf Windows-Clientcomputern?
1. Wie ändern Sie die PowerShell-Ausführungsrichtlinie?

## <a name="recommended-reading"></a>Empfohlene Lektüre

Wenn Sie weitere Informationen zu den in diesem Kapitel behandelten Themen wünschen, empfehle ich Ihnen, die folgenden PowerShell-Hilfethemen zu lesen.

- [about_Automatic_Variables][]
- [about_Execution_Policies][]

Im nächsten Kapitel erfahren Sie mehr über die Auffindbarkeit von Befehlen in PowerShell. Einer der Aspekte, der behandelt wird, ist, wie Sie PowerShell so aktualisieren, dass diese Hilfethemen direkt innerhalb der PowerShell angezeigt werden können, anstatt sie im Internet lesen zu müssen.

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Execution_Policies]: /powershell//powershell/module/microsoft.powershell.core/about/about_execution_policies
[Aktualisieren einer vorhandenen Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Installieren von PowerShell]: /powershell/scripting/install/installing-powershell
[Starten von Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
