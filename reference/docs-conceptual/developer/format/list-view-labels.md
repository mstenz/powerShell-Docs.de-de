---
title: Listenansicht (Bezeichnungen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53442bb1-74a3-49f9-9150-3bc3081a7565
caps.latest.revision: 6
ms.openlocfilehash: 27de41c88e224f7610c10a764e51524016ecc8cb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72362789"
---
# <a name="list-view-labels"></a>Listenansicht (Label)

Dieses Beispiel zeigt, wie Sie eine Listenansicht implementieren, in der eine benutzerdefinierte Bezeichnung für jede Zeile der Liste angezeigt wird. Diese Listenansicht zeigt die Eigenschaften des [System. ServiceProcess. ServiceController an? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekt, das vom Cmdlet " [Get-Service](/powershell/module/Microsoft.PowerShell.Management/Get-Service) " zurückgegeben wird. Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>So laden Sie diese Formatierungs Datei

1. Kopieren Sie den XML-Code aus dem Beispiel Abschnitt dieses Themas in eine Textdatei.

2. Speichern Sie die Textdatei. Stellen Sie sicher, dass Sie die Erweiterung "`format.ps1xml`" der Datei hinzufügen, um Sie als Formatierungs Datei zu identifizieren.

3. Öffnen Sie Windows PowerShell, und führen Sie den folgenden Befehl aus, um die Formatierungs Datei in die aktuelle Sitzung zu laden: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Mit dieser Formatierungs Datei wird die Anzeige eines Objekts definiert, das bereits durch eine Windows PowerShell-Formatierungs Datei definiert ist. Sie müssen den `prependPath`-Parameter verwenden, wenn Sie das Cmdlet ausführen, und Sie können diese Formatierungs Datei nicht als Modul laden.

## <a name="demonstrates"></a>Deutlich

Diese Formatierungs Datei veranschaulicht die folgenden XML-Elemente:

- Das [Name](./name-element-for-view-format.md) -Element für die Sicht.

- Das [viewselectedby](./viewselectedby-element-format.md) -Element, das definiert, welche Objekte von der Sicht angezeigt werden.

- Das [ListControl](./listcontrol-element-format.md) -Element, das definiert, welche Eigenschaft von der Ansicht angezeigt wird.

- Das [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) -Element, das definiert, was in einer Zeile der Listenansicht angezeigt wird.

- Das [Label](./label-element-for-listitem-for-listcontrol-format.md) -Element, das definiert, was in einer Zeile der Listenansicht angezeigt wird.

- Das [propertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) -Element, das definiert, welche Eigenschaft angezeigt wird.

## <a name="example"></a>Beispiel

Der folgende XML-Code definiert eine Listenansicht, in der in jeder Zeile eine benutzerdefinierte Bezeichnung angezeigt wird. In diesem Fall enthält die Bezeichnung den Eigenschaftsnamen, bei dem jeder Buchstabe groß geschrieben ist, und das Wort "Property". In jeder Zeile wird der Name der Eigenschaft angezeigt, gefolgt vom Wert der-Eigenschaft.

```xml
<Configuration>
  <ViewDefinitions>
    <View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>
          <ListItem>
            <Label>NAME property</Label>
            <PropertyName>Name</PropertyName>
          </ListItem>
          <ListItem>
            <Label>DISPLAYNAME property</Label>
            <PropertyName>DisplayName</PropertyName>
          </ListItem>
          <ListItem>
            <Label>STATUS property</Label>
            <PropertyName>Status</PropertyName>
          </ListItem>
          <ListItem>
            <Label>SERVICETYPE property</Label>
            <PropertyName>ServiceType</PropertyName>
          </ListItem>
        </ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>

  </ViewDefinitions>
</Configuration>
```

Das folgende Beispiel zeigt, wie Windows PowerShell [System. ServiceProcess. ServiceController anzeigt? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekte, nachdem diese Format Datei geladen wurde.

```powershell
Get-Service f*
```

```output
NAME property        : Fax
DISPLAYNAME property : Fax
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FCSAM
DISPLAYNAME property : Microsoft Antimalware Service
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : fdPHost
DISPLAYNAME property : Function Discovery Provider Host
STATUS property      : Stopped
SERVICETYPE property : Win32ShareProcess

NAME property        : FDResPub
DISPLAYNAME property : Function Discovery Resource Publication
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache
DISPLAYNAME property : Windows Font Cache Service
STATUS property      : Running
SERVICETYPE property : Win32ShareProcess

NAME property        : FontCache3.0.0.0
DISPLAYNAME property : Windows Presentation Foundation Font Cache 3.0.0.0
STATUS property      : Stopped
SERVICETYPE property : Win32OwnProcess

NAME property        : FSysAgent
DISPLAYNAME property : Microsoft Forefront System Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess

NAME property        : FwcAgent
DISPLAYNAME property : Firewall Client Agent
STATUS property      : Running
SERVICETYPE property : Win32OwnProcess
```

## <a name="see-also"></a>Weitere Informationen

[Beispiele für das Formatieren von Dateien](./examples-of-formatting-files.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
