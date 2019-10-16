---
title: Breite Ansicht (Basic) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9abb63b8-6d02-4e24-9c0e-2d15a04e9051
caps.latest.revision: 8
ms.openlocfilehash: 7a36f548a3eccdf2c9cad04a8bfe28bf4e8d6dfd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367939"
---
# <a name="wide-view-basic"></a>Breite Ansicht (Basic)

In diesem Beispiel wird gezeigt, wie eine grundlegende weite Ansicht implementiert wird, in der [System. ServiceProcess. ServiceController angezeigt wird? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekte, die vom Cmdlet "`Get-Service`" zurückgegeben werden. Weitere Informationen zu den Komponenten einer breiten Ansicht finden Sie unter [Erstellen einer breiten Ansicht](./creating-a-wide-view.md).

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

- Das [wideitem](./wideitem-element-for-widecontrol-format.md) -Element, das definiert, welche Eigenschaft von der Ansicht angezeigt wird.

## <a name="example"></a>Beispiel

Der folgende XML-Code definiert eine breite Ansicht, in der der Wert der [System. ServiceProcess. ServiceController. ServiceName](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) -Eigenschaft angezeigt wird.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Configuration>
  <ViewDefinitions>
    <View>
      <Name>ServiceWideView</Name>
      <ViewSelectedBy>
        <TypeName>System.ServiceProcess.ServiceController</TypeName>
      </ViewSelectedBy>
      <WideControl>
        <WideEntries>
          <WideEntry>
            <WideItem>
              <PropertyName>ServiceName</PropertyName>
            </WideItem>
          </WideEntry>
        </WideEntries>
      </WideControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

Das folgende Beispiel zeigt, wie Windows PowerShell [System. ServiceProcess. ServiceController anzeigt? Displayproperty = FullName](/dotnet/api/System.ServiceProcess.ServiceController) -Objekte, nachdem diese Format Datei geladen wurde.

```powershell
Get-Service f*
```

```output
Fax                      FCSAM
fdPHost                  FDResPub
FontCache                FontCache3.0.0.0
FSysAgent                FwcAgent
```

## <a name="see-also"></a>Weitere Informationen

[Beispiele für das Formatieren von Dateien](./examples-of-formatting-files.md)

[Schreiben einer PowerShell-Formatierungs Datei](./writing-a-powershell-formatting-file.md)
