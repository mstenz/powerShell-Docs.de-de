---
title: Hinzufügen von Ressourcen zu einem Management odata-Webdienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: 2f6ad8ee9f303d3dea92a633996e9248d2e87a21
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561899"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Hinzufügen von Ressourcen zu einem Management OData-Webdienst

In diesem Beispiel wird veranschaulicht, wie mithilfe des odata-Schema-Designers von Management eine Ressource zu einem vorhandenen verwaltungsodata-Webdienst hinzugefügt wird. Das [psexsrolebasedplugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) -Beispiel erstellt einen Webdienst, der die Prozess-und Server Ressourcen verfügbar macht. In diesem Beispiel fügen Sie dem Webdienst eine VM-Ressource (Virtual Machine, virtueller Computer) hinzu.

## <a name="prerequisites"></a>Voraussetzungen

In diesem Thema wird davon ausgegangen, dass Sie das Beispiel " [pswsrolebasedplugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) " heruntergeladen und installiert haben, wie unter [Erstellen eines Windows PowerShell-Webdiensts](./creating-a-management-odata-web-service.md)beschrieben, und dass Sie den [Management odata-Schema-Designer](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner)heruntergeladen und installiert haben. In diesem Thema wird auch davon ausgegangen, dass Sie das Hyper-V Windows PowerShell-Modul auf dem Computer installiert haben, auf dem Sie den odata-Verwaltungs Endpunkt einrichten.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Hinzufügen einer VM als Ressource zum Webdienst

Der erste Schritt besteht darin, das Schema aus dem vorhandenen Verwaltungs-odata-Endpunkt in den Schema-Designer zu importieren. Dies wird im folgenden Verfahren beschrieben.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importieren eines vorhandenen Schemas in den Schema-Designer

1. Öffnen Sie den Verwaltungs-odata-Schema-Designer.

2. Wählen Sie im Menü **Datei** die Option **Datei** aus. **Neu** ; **Datei**. Das Dialogfeld **neue Datei** wird angezeigt.

3. Klicken Sie auf **Verwaltung odata-Modell**, und klicken Sie dann auf **Öffnen**.

4. Klicken Sie mit der rechten Maustaste auf das Hauptfenster, und klicken Sie auf **Schema Datei** ;. **Importieren**Sie. Das Dialogfeld **Öffnen** wird angezeigt.

5. Navigieren Sie zu dem Ordner, in dem Sie den Management odata-Webdienst für das Beispiel " [pwaysrolebasedplugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) " einrichten. Wenn Sie das in diesem Beispiel bereitgestellte Windows PowerShell-Skript verwendet haben, um den Endpunkt einzurichten, ohne das Skript zu ändern, lautet der Ordner **c:\inetpub\wwwroot\mudata**. Wählen Sie Schema. MOF aus, und klicken Sie auf **Öffnen**.

   Öffnen Sie an diesem Punkt die Dateien "Schema. mof" und "Schema. xml" in einem Text-Editor, und beachten Sie, dass Sie Zuordnungen für die Prozess-und Dienst Ressourcen enthalten. Die Datei "Schema. mof" verwendet den MOF (Managed [Management Task Force](https://www.dmtf.org/) )-Standard (DTMF). Die Datei "Schema. xml" verwendet ein XML-Schema, das unter [Ressourcen Zuordnung Schema](./resource-mapping-schema.md)beschrieben wird.

   Im folgenden Verfahren wird beschrieben, wie Hyper-V-Cmdlets in in das Schema Modell importiert werden.

#### <a name="importing-cmdlets-into-the-schema"></a>Importieren von Cmdlets in das Schema

1. Klicken Sie mit der rechten Maustaste auf einen leeren Bereich des Fensters Schema-Designer, und klicken Sie dann auf **Cmdlets importieren**. Das Dialogfeld **Cmdlet-Import-Assistent** wird angezeigt.

2. Stellen Sie sicher, dass **lokaler Computer** ausgewählt ist, und klicken Sie auf **weiter**.

3. Stellen Sie sicher, dass installierte Windows PowerShell-Module ausgewählt ist, und wählen Sie in der Dropdown Liste die Option Hyper-V aus. Klicken Sie auf **Weiter**. Klicken Sie auf **Weiter**.

4. Wählen Sie in der **Cmdlet-Substantiv** Liste die Option **VM**aus. Klicken Sie auf **Weiter**.

5. In diesem Beispiel werden nur die Get-und DELETE-Befehle mit Cmdlets gebunden. Deaktivieren Sie die Kontrollkästchen **Erstellen** und **Aktualisieren** , und stellen Sie sicher, dass die Kontrollkästchen **Get** und **Delete** aktiviert sind. Stellen Sie sicher, dass das `Get-VM` Cmdlet für **Get**ausgewählt ist und das `Remove-VM` Cmdlet zum **Löschen**ausgewählt ist.

6. Da in den Metadaten für die VM-Cmdlets kein Ausgabetyp angegeben ist, müssen Sie das Cmdlet ausführen, um den Ausgabetyp anzugeben. Wählen Sie geben Sie den **Ausgabetyp** aus, und klicken Sie auf **Ausführen** Das Dialogfeld " **Cmdlet ausführen** " wird angezeigt. Klicken Sie auf **Ausführen**. Das Feld für den **CLR-Typ** wird mit dem `VirtualMachine` Typ aufgefüllt. Klicken Sie auf **OK**, und klicken Sie dann auf **weiter**.

7. Standardmäßig sind alle Eigenschaften des virtualmachine-Objekts ausgewählt. Sie können alle Eigenschaften löschen, die nicht als Teil der Daten angezeigt werden sollen, die zurückgegeben werden, wenn Sie diese Ressource vom Webdienst anfordern. Klicken Sie auf **Weiter**.

8. Sie müssen mindestens eine Eigenschaft auswählen, die als Schlüssel verwendet werden soll. Wählen Sie in der Liste **Name** aus, und klicken Sie auf **weiter**.

9. Im nächsten Fenster können Sie Eigenschaften der odata-Verwaltungs Ressource den Eigenschaften der zugrunde liegenden Cmdlets zuordnen. Der Assistent ordnet Eigenschaften standardmäßig identischen Namen zu. Beispielsweise wird die- `ComputerName` Eigenschaft der-Ressource der- `ComputerName` Eigenschaft der-Cmdlets zugeordnet.  Auf diese Weise können Sie die `ComputerName` -Eigenschaft in einer Anforderung an den Webdienst angeben und angeben, dass der angegebene Wert an das `Get-VM` Cmdlet übergeben werden soll. `Id`und `Name` werden standardmäßig ebenfalls zugeordnet.

   10. Klicken Sie auf **weiter**und dann auf **Fertig**stellen.

       Die VM-Ressource wird jetzt im Fenster Schema-Designer angezeigt. Sie können die Eigenschaften und Vorgänge untersuchen, die der Ressource zugeordnet sind. Als nächstes exportieren Sie die aktualisierten Schema Dateien in das virtuelle Verzeichnis für den Webdienst.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Exportieren von Schema Dateien aus dem Schema-Designer

1. Klicken Sie mit der rechten Maustaste auf einen leeren Bereich des Schema-Designer-Fensters, und klicken Sie auf **Schema Datei** ;. **Exportieren**. Das Dialogfeld **Speichern** unter wird angezeigt.

2. Navigieren Sie zu demselben Verzeichnis, in dem Sie die MOF-Datei importiert haben. Benennen Sie die Datei mit der ursprünglichen MOF-Datei (standardmäßig "Schema. mof"), und klicken Sie auf **Speichern**. Vergewissern Sie sich, dass Sie die vorhandene Datei überschreiben möchten.

   Obwohl Sie im Dialogfeld **Speichern** unter nicht explizit angegeben ist, werden dadurch sowohl die Schema. MOF-als auch die Schema. XML-Dateien ersetzt.

## <a name="next-steps"></a>Nächste Schritte

Bevor Sie über den odata-Webdienst für die Verwaltung auf die neue VM-Ressource zugreifen, müssen Sie die Datei rbacconfiguration. xml aktualisieren, um den Zugriff auf das Hyper-V-Windows PowerShell-Modul zu ermöglichen, wie unter [Konfigurieren der rollenbasierten Autorisierung](./configuring-role-based-authorization.md)beschrieben. Außerdem müssen Sie den Webdienst neu starten.
