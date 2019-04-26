---
title: Hinzufügen von Ressourcen zu einem Management OData-Webdienst | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080780"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Hinzufügen von Ressourcen zu einem Management OData-Webdienst

In diesem Beispiel wird veranschaulicht, wie beim Hinzufügen einer Ressource zu einem vorhandenen Management OData-Webdienst, mit dem Management OData-Schema-Designer wird. Die [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) Beispiel erstellt einen Webdienst, der den Prozess und Serverressourcen verfügbar macht. In diesem Beispiel fügen Sie eine Ressource des virtuellen Computers (VM) an den Webdienst hinzu.

## <a name="prerequisites"></a>Voraussetzungen

In diesem Thema wird davon ausgegangen, dass Sie heruntergeladen und installiert die [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) Beispiel, wie in beschrieben [Erstellen eines Windows PowerShell-Webdiensts](./creating-a-management-odata-web-service.md), und die Sie heruntergeladen und installiert haben die [Management OData-Schema-Designer](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). In diesem Thema wird davon ausgegangen, dass Sie das Hyper-V Windows PowerShell-Modul, das auf dem Computer installiert, in dem Sie den Management-Odata-Endpunkt eingerichtet, haben.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Hinzufügen des virtuellen Computers als eine Ressource mit dem Webdienst

Der erste Schritt ist das Schema aus den vorhandenen Management OData-Endpunkt in der Schema-Designer zu importieren. Das folgende Verfahren beschreibt, wie das geht.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importieren ein vorhandenes Schema in der Schema-designer

1. Den Management-OData-Schema-Designer zu öffnen.

2. Von der **Datei** , wählen Sie im Menü **Datei** ; **Neue** ; **Datei**. Die **neue Datei** Dialogfeld wird angezeigt.

3. Klicken Sie auf **Management OData-Modell**, und klicken Sie dann auf **öffnen**.

4. Mit der rechten Maustaste im Hauptfenster von, und klicken Sie auf **Schemadatei** ; **Import**. Die **öffnen** Dialogfeld wird angezeigt.

5. Navigieren Sie zu dem Ordner, in dem Sie den Management-OData-Webdienst für einrichten, der [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) Beispiel. Wenn Sie das Windows PowerShell-Skript, das im Lieferumfang dieses Beispiels verwendet, um den Endpunkt einrichten, ohne das Skript ändern, wird der Ordner ist **C:\inetpub\wwwroot\Modata**. Wählen Sie Schema.mof aus, und klicken Sie auf **öffnen**.

   An diesem Punkt öffnen Sie die Schema.mof und "Schema.xml"-Dateien in einem Text-Editor, und beachten Sie, dass sie die Zuordnungen für den Prozess und Dienst-Ressourcen enthalten. Verwendet die Datei "Schema.mof" [Distributed Management Task Force](https://www.dmtf.org/) (MFV) MOF (Managed Object)-Standard. Die Datei "schema.xml" verwendet ein XML-Schema, das beschrieben ist [Ressourcenschema Zuordnung](./resource-mapping-schema.md).

   Das folgende Verfahren beschreibt, wie zum Importieren von Hyper-V-Cmdlets in in das Schemamodell wird.

#### <a name="importing-cmdlets-into-the-schema"></a>Importieren von Cmdlets in das schema

1. Mit der rechten Maustaste auf einen leeren Bereich im Schema-Designer-Fenster, und klicken Sie auf **Import-Cmdlets**. Die **Cmdlet Import-Assistenten** Dialogfeld wird angezeigt.

2. Stellen Sie sicher, dass **lokalen Computer** ausgewählt ist, und klicken Sie auf **Weiter**.

3. Stellen Sie sicher, dass Windows PowerShell-Module installiert ausgewählt ist, und wählen Sie Hyper-V, aus der Dropdown-Liste. Klicken Sie auf **Weiter**. Klicken Sie auf **Weiter**.

4. In der **Cmdlet-Nomen** Liste **VM**. Klicken Sie auf **Weiter**.

5. In diesem Beispiel werden wir nur die Get- und Delete-Befehle mit Cmdlets binden. Deaktivieren der **erstellen** und **UPDATE** Kontrollkästchen, und stellen Sie sicher, dass die **erhalten** und **löschen** Kontrollkästchen aktiviert sind. Stellen Sie sicher, dass die `Get-VM` Cmdlet ausgewählt ist **erhalten**, und die `Remove-VM` Cmdlet ausgewählt ist **löschen**.

6. Da die Metadaten für die Cmdlets des virtuellen Computers keinen Ausgabetyp angegeben ist, müssen Sie führen Sie das Cmdlet, um den Ausgabetyp angeben. Wählen Sie **Ausgabetyp angeben** , und klicken Sie auf **führen Cmdlet**. Die **ausführen Cmdlet** Dialogfeld wird angezeigt. Klicken Sie auf **ausführen**. Die **CLR-Typ** Feld wird gefüllt, mit der `VirtualMachine` Typ. Klicken Sie auf **OK**, klicken Sie dann auf **Weiter**.

7. Standardmäßig werden alle Eigenschaften des Objekts VirtualMachine ausgewählt werden. Sie können alle Eigenschaften löschen, die Sie nicht als Teil der Daten, die zurückgegeben werden, wenn Sie diese Ressource vom Webdienst anfordern möchten. Klicken Sie auf **Weiter**.

8. Sie müssen mindestens eine Eigenschaft als Schlüssel verwendet werden, auswählen. Wählen Sie **Namen** in der Liste aus, und klicken Sie auf **Weiter**.

9. Im nächste Fenster können Sie Eigenschaften der zugrunde liegenden Cmdlets Eigenschaften der Management-OData-Ressource zugeordnet. Der Assistent ordnet Eigenschaften mit identischem Namen in der Standardeinstellung an. Z. B. die `ComputerName` -Eigenschaft der Ressource zugeordnet ist die `ComputerName` Eigenschaft der-Cmdlets.  Dies ermöglicht Ihnen die Angabe der `ComputerName` Eigenschaft in einer Anforderung an den Webdienst, und von Ihnen angegebene Wert übergeben werden, um die `Get-VM` Cmdlet. `Id` und `Name` werden auch standardmäßig zugeordnet.

   10. Klicken Sie auf **Weiter**, klicken Sie dann auf **Fertig stellen**.

       Die VM-Ressource wird jetzt im Fenster Schema-Designers angezeigt. Sie können die Eigenschaften und Operationen zur Ressource zugeordnete überprüfen. Als Nächstes exportieren Sie die aktualisierte Schema-Dateien in das virtuelle Verzeichnis für den Webdienst.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Exportieren von Schemadateien aus der Schema-designer

1. Mit der rechten Maustaste auf einen leeren Bereich im Schema-Designer-Fenster, und klicken Sie auf **Schemadatei** ; **Exportieren**. Die **speichern** Dialogfeld wird angezeigt.

2. Navigieren Sie in dasselbe Verzeichnis, in dem Sie die MOF-Datei importiert. Nennen Sie die Datei identisch mit der ursprünglichen MOF-Datei (standardmäßig Schema.mof), und klicken Sie auf **speichern**. Vergewissern Sie sich, dass Sie die vorhandene Datei überschreiben möchten.

   Obwohl es im nicht explizit angegeben ist die **speichern** Dialogfeld dies ersetzt den Schema.mof "Schema.xml" Dateien und.

## <a name="next-steps"></a>Nächste Schritte

Bevor Sie die neue VM-Ressource aus dem Management-OData-Webdienst zugreifen, müssen Sie die RbacConfiguration.xml-Datei, um den Zugriff auf dem Hyper-V Windows PowerShell-Modul zu ermöglichen, wie in beschrieben aktualisieren [Konfigurieren der rollenbasierten Autorisierung](./configuring-role-based-authorization.md), und Sie müssen auch den Webdienst neu zu starten.