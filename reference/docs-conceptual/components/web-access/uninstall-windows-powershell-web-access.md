---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: Deinstallieren von Windows PowerShell Web Access
ms.openlocfilehash: 3c2c83525f5a240976eef215b5eac939796c91e8
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279009"
---
# <a name="uninstall-windows-powershell-web-access"></a>Deinstallieren von Windows PowerShell Web Access

Aktualisiert: 24. Juni 2013

Gilt für: Windows Server 2012 R2, Windows Server 2012

Mit den Schritten in diesem Thema entfernen Sie die Windows PowerShell Web Access-Website und die zugehörige Anwendung von dem Gatewayserver, auf dem diese installiert sind.

## <a name="notify-users"></a>Benachrichtigen von Benutzern

Benachrichtigen Sie zuvor die Benutzer der webbasierten Konsole, die Sie von der Website entfernen möchten.

Bei der Deinstallation von Windows PowerShell Web Access werden IIS oder andere Features, die automatisch installiert wurden, nicht deinstalliert, weil diese von Windows PowerShell Web Access zur Ausführung benötigt werden. Beim Deinstallationsvorgang bleiben die Features unangetastet, mit denen für Windows PowerShell Web Access eine Abhängigkeit besteht. Sie können diese Features bei Bedarf separat deinstallieren.

## <a name="recommended-quick-uninstallation"></a>Empfohlene (schnelle) Deinstallation

Mit den in diesem Abschnitt beschriebenen Verfahren können Sie Folgendes deinstallieren:

- Die Windows PowerShell Web Access-Anwendung und
- das Windows PowerShell Web Access-Feature

, indem Sie Windows PowerShell-Cmdlets verwenden.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Schritt 1: Löschen der Webanwendung mithilfe von Cmdlets

1. Öffnen Sie eine Windows PowerShell-Sitzung, indem Sie einen der folgenden Schritte durchführen.

   - Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste auf der Taskleiste auf **Windows PowerShell**.
   - Klicken Sie auf der Windows-**Startseite** auf **Windows PowerShell**.

2. Geben Sie `Uninstall-PswaWebApplication` ein, und drücken Sie dann die **EINGABETASTE**.

   1. Wenn Sie Ihren eigenen, benutzerdefinierten Websitenamen angegeben haben, fügen Sie dem Befehl den Parameter `-WebsiteName` hinzu, und geben Sie den Namen der Website an.

      `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`

   1. Wenn Sie eine benutzerdefinierte Webanwendung (und nicht die Standardanwendung **pswa**) verwendet haben, fügen Sie dem Befehl den `-WebApplicationName`-Parameter hinzu, und geben Sie den Namen der Webanwendung an.

      `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`

   1. Fügen Sie dem Cmdlet den Parameter `DeleteTestCertificate` hinzu, falls Sie ein Testzertifikat verwenden. Dies ist im folgenden Beispiel dargestellt.

      `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Schritt 2: Deinstallieren von Windows PowerShell Web Access mithilfe von Cmdlets

1. Öffnen Sie eine Windows PowerShell-Sitzung mit erhöhten Benutzerrechten, indem Sie einen der folgenden Schritte durchführen. Wenn bereits eine Sitzung geöffnet ist, fahren Sie mit dem nächsten Schritt fort.

    - Klicken Sie auf dem Windows-Desktop mit der rechten Maustaste in der Taskleiste auf **Windows PowerShell** und anschließend auf **Als Administrator ausführen**.
    - Klicken Sie auf dem Windows-**Startbildschirm** mit der rechten Maustaste auf **Windows PowerShell**, und klicken Sie anschließend auf **Als Administrator ausführen**.

1. Geben Sie Folgendes ein, und drücken Sie dann die **EINGABETASTE**, wobei *computer_name* für einen Remoteserver steht, von dem Sie Windows PowerShell Web Access entfernen möchten. Mit dem Parameter `-Restart` werden Zielserver automatisch neu gestartet, falls dies für das Entfernen erforderlich ist.

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart`

    Zum Entfernen von Rollen oder Features von einer Offline-VHD müssen Sie die Parameter `-ComputerName` und `-VHD` hinzufügen. Der Parameter `-ComputerName` enthält den Namen des Servers, auf dem die VHD eingebunden werden soll. Der Parameter `-VHD` enthält den Pfad zur VHD-Datei auf dem angegebenen Server.

    `Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart`

1. Vergewissern Sie sich nach Abschluss der Entfernung, ob Windows PowerShell Web Access wirklich entfernt wurde. Öffnen Sie dazu im Server-Manager die Seite **Alle Server**, wählen Sie einen Server aus, von dem Sie das Feature entfernt haben, und zeigen Sie auf der Seite für den ausgewählten Server die Kachel **Rollen und Features** an.

    Sie können auch das Cmdlet `Get-WindowsFeature` für den ausgewählten Server auswählen (Get-WindowsFeature -ComputerName &lt;*Computername*&gt;), um eine Liste der auf dem Server installierten Rollen und Features anzuzeigen.

## <a name="custom-uninstallation"></a>Benutzerdefinierte Deinstallation

Mit den in diesem Abschnitt beschriebenen Verfahren können Sie die Windows PowerShell Web Access-Webanwendung und die Windows PowerShell Web Access-Funktion mit dem Assistenten zum Entfernen von Rollen und Features im Server-Manager und der IIS Manager-Konsole deinstallieren.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Schritt 1: Löschen der Webanwendung mithilfe von IIS-Manager

1. Öffnen Sie die IIS-Manager-Konsole, indem Sie eine der folgenden Aktionen ausführen: Wenn die Konsole bereits geöffnet ist, fahren Sie mit dem nächsten Schritt fort.

   - Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken. Klicken Sie im Menü **Tools** im Server-Manager auf **Internetinformationsdienste-Manager (IIS)** .

   - Geben Sie auf dem Windows-**Startbildschirm** einen beliebigen Teil des Namens **Internetinformationsdienste-Manager (IIS)** ein. Klicken Sie auf die Verknüpfung, wenn diese in den **Apps**-Ergebnissen angezeigt wird.

1. Wählen Sie im IIS-Manager-Strukturbereich die Website aus, auf der die Windows PowerShell Web Access-Webanwendung ausgeführt wird.

1. Klicken Sie im **Aktionsbereich** unter **Website verwalten** auf **Beenden**.

1. Klicken Sie im Strukturbereich mit der rechten Maustaste auf die Webanwendung der Website, von der die Windows PowerShell Web Access-Webanwendung ausgeführt wird, und klicken Sie dann auf **Entfernen**.

1. Wählen Sie im Strukturbereich die Option **Anwendungspools** und dann den Windows PowerShell Web Access-Anwendungsordner aus, klicken Sie im **Aktionsbereich** auf **Beenden**, und klicken Sie im Inhaltsbereich dann auf **Entfernen**.

1. Schließen Sie den IIS-Manager.

   > [!WARNING]
   > Das Zertifikat wird während der Deinstallation nicht gelöscht. Wenn Sie ein selbstsigniertes Zertifikat erstellt oder ein Testzertifikat verwendet haben und dieses Zertifikat nun entfernen möchten, müssen Sie es im IIS-Manager löschen.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Schritt 2: Deinstallieren von Windows PowerShell Web Access mithilfe des Assistenten zum Entfernen von Rollen und Features

1. Wenn der Server-Manager bereits geöffnet ist, fahren Sie mit dem nächsten Schritt fort. Ist der Server-Manager noch nicht geöffnet, öffnen Sie ihn mit einer der folgenden Aktionen.

    - Starten Sie auf dem Windows-Desktop den Server-Manager, indem Sie in der Windows-Taskleiste auf **Server-Manager** klicken.
    - Klicken Sie auf der Windows-**Startseite** auf **Server-Manager**.

1. Klicken Sie im Menü **Verwalten** auf **Rollen und Funktionen entfernen**.

1. Wählen Sie auf der Seite **Zielserver auswählen** den Server oder die Offline-VHD aus, von dem bzw. der Sie das Feature entfernen möchten. Um eine Offline-VHD auszuwählen, müssen Sie zuerst den Server auswählen, auf dem die VHD eingebunden werden soll. Wählen Sie anschließend die VHD-Datei aus. Klicken Sie nach dem Auswählen des Zielservers auf **Weiter**.

1. Klicken Sie erneut auf **Weiter**, um auf die Seite **Features entfernen** zu wechseln.

1. Deaktivieren Sie das Kontrollkästchen unter **Windows PowerShell Web Access**, und klicken Sie auf **Weiter**.

1. Klicken Sie auf der Seite **Entfernungsauswahl bestätigen** auf **Entfernen**.

## <a name="see-also"></a>Weitere Informationen

- [Install and Use Windows PowerShell Web Access (Installieren und Verwenden von Windows PowerShell Web Access)](install-and-use-windows-powershell-web-access.md)
- [IIS Manager 7.0 Help (Hilfe zum IIS-Manager 7.0)](https://technet.microsoft.com/library/cc732664.aspx)