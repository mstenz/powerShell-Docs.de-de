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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083738"
---
# <a name="wide-view-basic"></a>Breite Ansicht (Basic)

In diesem Beispiel wird gezeigt, wie eine grundlegende Breite Ansicht zu implementieren, die zeigt die [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) zurückgegebenen Objekte die `Get-Service` Cmdlet. Weitere Informationen zu den Komponenten der eine Breite Ansicht, finden Sie unter [erstellen eine Breite Ansicht](./creating-a-wide-view.md).

### <a name="to-load-this-formatting-file"></a>Laden Sie diese Formatierungsdatei

1. Kopieren Sie den XML-Code in eine Textdatei aus dem Abschnitt "Beispiel" dieses Themas.

2. Speichern Sie die Textdatei ein. Achten Sie darauf, dass Sie zum Hinzufügen der `format.ps1xml` Erweiterung der Datei, die sie als eine Formatierungsdatei zu identifizieren.

3. Öffnen Sie Windows PowerShell, und führen Sie den folgenden Befehl aus, um die Formatierungsdatei in der aktuellen Sitzung zu laden: `Update-formatdata -prependpath PathToFormattingFile`.

   > [!WARNING]
   > Diese Formatierung Datei definiert die Anzeige eines Objekts, das bereits von einer Windows PowerShell-Formatierung-Datei definiert ist. Verwenden Sie die `prependPath` Parameter an, wenn Sie das Cmdlet ausführen, und Sie nicht werden diese Formatierung geladen können Datei als Modul.

## <a name="demonstrates"></a>Zeigt

Diese Formatierung Datei veranschaulicht die folgenden XML-Elemente:

- Die [Namen](./name-element-for-view-format.md) -Element für die Ansicht.

- Die [ViewSelectedBy](./viewselectedby-element-format.md) -Element, das definiert, welche Objekte von der Ansicht angezeigt werden.

- Die [WideItem](./wideitem-element-for-widecontrol-format.md) -Element, das definiert, welche Eigenschaft von der Ansicht angezeigt wird.

## <a name="example"></a>Beispiel

Das folgende XML definiert eine Breite Ansicht, die den Wert der [System.Serviceprocess.Servicecontroller.Servicename](/dotnet/api/System.ServiceProcess.ServiceController.ServiceName) Eigenschaft.

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

Das folgende Beispiel zeigt, wie Windows PowerShell zeigt den [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Objekte nach dem Laden dieser Formatdatei.

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

[Beispiele für die Formatierungsdateien](./examples-of-formatting-files.md)

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
