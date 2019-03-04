---
title: Listenansicht (Basic) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 918f381c-43e6-4594-a468-a40bfa8a16d6
caps.latest.revision: 7
ms.openlocfilehash: 1c683693c331ccfaf7355a0dd51801ed6fd39b3b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853306"
---
# <a name="list-view-basic"></a>Listenansicht (Basic)

Dieses Beispiel zeigt, wie Sie eine einfache Listenansicht zu implementieren, die zeigt die [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) zurückgegebenen Objekte die [Get-Service](/powershell/module/microsoft.powershell.management/get-service) Cmdlet. Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).
Dieses Beispiel zeigt, wie Sie eine einfache Listenansicht zu implementieren, die zeigt die [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) zurückgegebenen Objekte die [Get-Service](/powershell/module/microsoft.powershell.management/get-service) Cmdlet. Weitere Informationen zu den Komponenten einer Listenansicht finden Sie unter [Erstellen einer Listenansicht](./creating-a-list-view.md).

### <a name="to-load-this-formatting-file"></a>Laden Sie diese Formatierungsdatei

1. Kopieren Sie den XML-Code in eine Textdatei aus dem Abschnitt "Beispiel" dieses Themas.

2. Speichern Sie die Textdatei ein. Achten Sie darauf, dass Sie zum Hinzufügen der `format.ps1xml` Erweiterung der Datei, die sie als eine Formatierungsdatei zu identifizieren.

3. Öffnen Sie Windows PowerShell, und führen Sie den folgenden Befehl aus, um die Formatierungsdatei in der aktuellen Sitzung zu laden: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Diese Formatierung Datei definiert die Anzeige eines Objekts, das bereits von einer Windows PowerShell-Formatierung-Datei definiert ist. Verwenden Sie die `prependPath` Parameter an, wenn Sie das Cmdlet ausführen, und Sie nicht werden diese Formatierung geladen können Datei als Modul.

## <a name="demonstrates"></a>Veranschaulicht

Diese Formatierung Datei veranschaulicht die folgenden XML-Elemente:

- Die [Namen](./name-element-for-view-format.md) -Element für die Ansicht.

- Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element, das definiert, welche Objekte von der Ansicht angezeigt werden.

- Die [ListControl](./listcontrol-element-format.md) -Element, das definiert, welche Eigenschaft von der Ansicht angezeigt wird.

- Die [ListItem](./listitem-element-for-listitems-for-listcontrol-format.md) Element, das definiert, was in einer Zeile in der Listenansicht angezeigt wird.

- Die [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) -Element, das definiert, welche Eigenschaft angezeigt wird.

## <a name="example"></a>Beispiel

Das folgende XML definiert eine Listenansicht, in dem vier Eigenschaften angezeigt. die [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekt. In jeder Zeile wird der Name der Eigenschaft gefolgt vom Wert der Eigenschaft angezeigt.

```xml
<Configuration>
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
              <PropertyName>Name</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>DisplayName</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>Status</PropertyName>
            </ListItem>
            <ListItem>
              <PropertyName>ServiceType</PropertyName>
            </ListItem>
          </ListItems>
        </ListEntry>
      </ListEntries>
    </ListControl>
  </View>
</Configuration>
```

Das folgende Beispiel zeigt, wie Windows PowerShell zeigt den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekte nach dem Laden dieser Formatdatei.

```powershell
Get-Service f*
```

```output
Name        : Fax
DisplayName : Fax
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FCSAM
DisplayName : Microsoft Antimalware Service
Status      : Running
ServiceType : Win32OwnProcess

Name        : fdPHost
DisplayName : Function Discovery Provider Host
Status      : Stopped
ServiceType : Win32ShareProcess

Name        : FDResPub
DisplayName : Function Discovery Resource Publication
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache
DisplayName : Windows Font Cache Service
Status      : Running
ServiceType : Win32ShareProcess

Name        : FontCache3.0.0.0
DisplayName : Windows Presentation Foundation Font Cache 3.0.0.0
Status      : Stopped
ServiceType : Win32OwnProcess

Name        : FSysAgent
DisplayName : Microsoft Forefront System Agent
Status      : Running
ServiceType : Win32OwnProcess

Name        : FwcAgent
DisplayName : Firewall Client Agent
Status      : Running
ServiceType : Win32OwnProcess
```

## <a name="see-also"></a>Weitere Informationen

[Beispiele für die Formatierungsdateien](./examples-of-formatting-files.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
