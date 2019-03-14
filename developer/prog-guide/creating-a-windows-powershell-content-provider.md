---
title: Erstellen eines Anbieters der Windows PowerShell-Inhalte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- content providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], content provider
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
caps.latest.revision: 6
ms.openlocfilehash: 1bccbfab55f4ba4476678b130bd9db91eed7df80
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795316"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Erstellen eines Windows PowerShell-Inhaltsanbieters

Dieses Thema beschreibt, wie Sie einen Windows PowerShell-Anbieter erstellen, der dem Benutzer ermöglicht, den Inhalt der Elemente in einem Datenspeicher zu bearbeiten. Daher ist ein Anbieter, der den Inhalt von Elementen zu bearbeiten, kann als eine Windows PowerShell-Inhaltsanbieter bezeichnet.

> [!NOTE]
> Sie können die C# Quelldatei (AccessDBSampleProvider06.cs) für diesen Anbieter, die mit dem Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten. Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladene Quelldateien stehen in der  **\<PowerShell-Beispiele >** Verzeichnis.
>
> Weitere Informationen zu anderen Implementierungen der Windows PowerShell-Anbieter, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md).

Die folgende Liste enthält die Abschnitte in diesem Thema. Wenn Sie mit dem Schreiben von Windows PowerShell-Inhaltsanbieter nicht vertraut sind, lesen Sie diese Abschnitte in der angezeigten Reihenfolge. Allerdings Sie mit dem Schreiben von Windows PowerShell-Inhaltsanbieter vertraut sind, fahren Sie direkt auf die Informationen, die Sie benötigen.

- [Definieren die Windows PowerShell-Inhalte Provider-Klasse](#Define-the-Windows-PowerShell-Content-Provider-Class)

- [Definiert die grundlegenden Funktionen](#Define-Functionality-of-Base-Class)

- [Implementieren einen Content-Reader](#Implementing-a-Content-Reader)

- [Implementieren einen Content-Writer](#Implementing-a-Content-Writer)

- [Abrufen des Inhalte Readers](#Retrieving-the-Content-Reader)

- [Anfügen von dynamische Parametern zu der `Get-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-Content-Cmdlet)

- [Abrufen des Inhalte Writers](#Retrieving-the-Content-Writer)

- [Anfügen von dynamischen Parametern an die Add_Content und `Set-Content` Cmdlets](#Attaching-Dynamic-Parameters-to-the-Add-Content-and-Set-Content-Cmdlets)

- [Löschen von Inhalt](#Clearing-Content)

- [Anfügen von dynamische Parametern zu der `Clear-Content` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-Content-Cmdlet)

- [Codebeispiel](#Code-Sample)

- [Definieren von Objekttypen und Formatierung](#defining-object-types-and-formatting)

- [Erstellen den Windows PowerShell-Anbieter](#Building-the-Windows-PowerShell-Provider)

- [Testen des Windows PowerShell-Anbieters](#Testing-the-Windows-PowerShell-Provider)

## <a name="define-the-windows-powershell-content-provider-class"></a>Definieren Sie die Windows PowerShell-Inhalte Provider-Klasse

Ein Windows PowerShell-Inhaltsanbieter muss erstellen Sie eine .NET-Klasse, die unterstützt die [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) Schnittstelle. Hier ist die Definition der Klasse für den elementanbieter, die in diesem Abschnitt beschrieben.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L32-L33 "AccessDBProviderSample06.cs")]

Beachten Sie, dass diese Klasse die Definition der [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) Attribut enthält zwei Parameter. Der erste Parameter gibt einen benutzerfreundlichen Namen für den Anbieter, der von Windows PowerShell verwendet wird. Der zweite Parameter gibt die spezifischen Windows PowerShell-Funktionen, die der Anbieter für die Windows PowerShell-Laufzeit während der befehlsverarbeitung verfügbar macht. Für diesen Anbieter sind keine hinzugefügten bestimmten Funktionen von Windows PowerShell.

## <a name="define-functionality-of-base-class"></a>Definieren Sie die Funktionalität der Basisklasse

Siehe [Entwurf der Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Klasse leitet sich von anderen Klassen, die bereitgestellt Funktionalität der anderen Anbieter. Ein Windows PowerShell-Inhaltsanbieter, definiert daher in der Regel mit alle Funktionen, die von diesen Klassen bereitgestellt werden.

Weitere Informationen zum Implementieren von Funktionen, die sitzungsspezifischen Initialisierungsinformationen hinzufügen und Freigeben von Ressourcen, die vom Anbieter verwendet werden, finden Sie unter [erstellen einen einfachen Windows PowerShell-Anbieter](./creating-a-basic-windows-powershell-provider.md). Allerdings können die meisten Anbieter, einschließlich des hier beschriebenen Anbieters die standardmäßige Implementierung dieser Funktionalität, die von Windows PowerShell bereitgestellt wird.

Der Anbieter muss der Datenspeicher für den Zugriff auf die Methoden implementieren die [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Basisklasse. Weitere Informationen zu diesen Methoden implementiert werden, finden Sie unter [erstellen ein Windows PowerShell-Laufwerk-Anbieter](./creating-a-windows-powershell-drive-provider.md).

Der Anbieter muss zum Bearbeiten der Elemente von einem Datenspeicher, z. B. abrufen, festlegen und Löschen von Elementen, die vom bereitgestellten Methoden implementieren die [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) Basisklasse. Weitere Informationen zu diesen Methoden implementiert werden, finden Sie unter [erstellen eine Windows PowerShell-Elementanbieter](./creating-a-windows-powershell-item-provider.md).

Um in Datenspeichern mit mehreren Ebenen zu arbeiten, der Anbieter muss von bereitgestellten Methoden implementieren die [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) Basisklasse. Weitere Informationen zu diesen Methoden implementiert werden, finden Sie unter [erstellen eine Windows PowerShell-Containeranbieter](./creating-a-windows-powershell-container-provider.md).

Der Anbieter muss um rekursive Befehle, geschachtelte Container und relative Pfade zu unterstützen, implementieren die [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Basisklasse. Darüber hinaus können diese Windows PowerShell-Inhaltsanbieter fügt [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) Schnittstelle zu den [ System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) Basisklasse und muss daher die von dieser Klasse bereitgestellten Methoden implementieren. Weitere Informationen finden Sie diese Methoden implementieren, finden Sie unter [implementieren Sie eine Windows PowerShell-Navigationsanbieter](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementieren einen Content-Reader

Zum Lesen von Inhalt aus einem Element implementiert ein Anbieter muss eine abgeleitete Readerklasse Content [System.Management.Automation.Provider.Icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader). Der Content-Reader für diesen Anbieter ermöglicht den Zugriff auf den Inhalt einer Zeile in einer Datentabelle. Die Content Readerklasse definiert eine **lesen** -Methode, ruft die Daten aus der angegebenen Zeile ab und gibt eine Liste darstellt, diese Daten, eine **Seek** -Methode, die der Content-Reader, wechselt ein  **Schließen** -Methode, die den Inhalt Leser und schließt und eine **Dispose** Methode.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2115-L2241 "AccessDBProviderSample06.cs")]

## <a name="implementing-a-content-writer"></a>Implementieren einen Content-Writer

Um Inhalt zu einem Element zu schreiben, muss ein Anbieter implementiert einen Inhalt Writerklasse leitet sich von [System.Management.Automation.Provider.Icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter). Die Content Writerklasse definiert eine **schreiben** Methode, die den Inhalt des angegebenen Zeile, schreibt eine **Seek** Methode, die den Inhalt Writer, verschiebt eine **schließen** -Methode, die geschlossen wird die Content-Writer, und ein **Dispose** Methode.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L2250-L2394 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-reader"></a>Abrufen des Inhalte Readers

Um Inhalt aus einem Element zu erhalten, muss der Anbieter implementieren die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) zur Unterstützung der `Get-Content` Cmdlet. Diese Methode gibt den Inhalt Reader für das Element am angegebenen Pfad zurück. Das Reader-Objekt kann dann den Inhalt Lesen geöffnet werden.

Dies ist die Implementierung von [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) für diese Methode für diesen Anbieter.

```csharp
public IContentReader GetContentReader(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be obtained only for tables");
    }

    return new AccessDBContentReader(path, this);
} // GetContentReader
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1829-L1846 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Punkte zu beachten, die zum Implementieren von GetContentReader

Möglicherweise gelten die folgenden Bedingungen zu einer Implementierung von [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-Inhaltsanbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) Methode muss sicherstellen, dass der Pfad, an die Methode übergebene die Anforderungen der angegebenen erfüllt Funktionen. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht abgerufen werden einen Reader für Objekte, die vom Benutzer ausgeblendet werden, es sei denn, die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Ein Fehler geschrieben werden soll, wenn Sie den Pfad ein Elements darstellt, die vom Benutzer ausgeblendet ist und [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) nastaven NA hodnotu `false`.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Das Cmdlet "Get-Content" Anfügen dynamische Parameter

Die `Get-Content` Cmdlet möglicherweise zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Um diese dynamischen Parameter zu gewährleisten, muss der Windows PowerShell-Inhaltsanbieter implementieren die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) Methode. Diese Methode ruft die dynamischen Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, das Cmdlet den Parameter hinzu.

Diese Windows-PowerShell-Containeranbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1853-L1856 "AccessDBProviderSample06.cs")]

## <a name="retrieving-the-content-writer"></a>Abrufen des Inhalte Writers

Um Inhalt zu einem Element zu schreiben, muss der Anbieter implementieren die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) zur Unterstützung der `Set-Content` und `Add-Content` Cmdlets. Diese Methode gibt den Content-Writer für das Element am angegebenen Pfad zurück.

Dies ist die Implementierung von [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) für diese Methode.

```csharp
public IContentWriter GetContentWriter(string path)
{
    string tableName;
    int rowNumber;

    PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

    if (type == PathType.Invalid)
    {
        ThrowTerminatingInvalidPathException(path);
    }
    else if (type == PathType.Row)
    {
        throw new InvalidOperationException("contents can be added only to tables");
    }

    return new AccessDBContentWriter(path, this);
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1863-L1880 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Punkte zu beachten, die zum Implementieren von GetContentWriter

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-Inhaltsanbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriter*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) Methode muss sicherstellen, dass der Pfad, an die Methode übergebene die Anforderungen der angegebenen erfüllt Funktionen. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht abgerufen werden einen Writer für Objekte, die vom Benutzer ausgeblendet werden, es sei denn, die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Ein Fehler geschrieben werden soll, wenn Sie den Pfad ein Elements darstellt, die vom Benutzer ausgeblendet ist und [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) nastaven NA hodnotu `false`.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Anfügen von dynamischen Parametern für die Add-Content und Set-Content-Cmdlets

Die `Add-Content` und `Set-Content` Cmdlets möglicherweise zusätzliche dynamische Parametern, die eine Laufzeit hinzugefügt werden. Um diese dynamischen Parameter zu gewährleisten, muss der Windows PowerShell-Inhaltsanbieter implementieren die [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) Methode, um diese zu verarbeiten Parameter. Diese Methode ruft die dynamischen Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt die Parameter der Cmdlets hinzufügen.

Diese Windows-PowerShell-Containeranbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1887-L1890 "AccessDBProviderSample06.cs")]

## <a name="clearing-content"></a>Löschen von Inhalt

Die Inhaltsanbieter implementiert die [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) Methode Unterstützung des der `Clear-Content` Cmdlet. Diese Methode entfernt den Inhalt des Elements am angegebenen Pfad, aber das Element bleiben intakt.

Dies ist die Implementierung von der [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) Methode für diesen Anbieter.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1775-L1812 "AccessDBProviderSample06.cs")]

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Punkte zu beachten, die zum Implementieren von ClearContent

Möglicherweise gelten die folgenden Bedingungen zu einer Implementierung von [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-Inhaltsanbieter von Funktionen des Anbieters der ExpandWildcards, Filter, einschließen oder ausschließen, deklarieren die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities)Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) Methode muss sicherstellen, dass der Pfad, an die Methode übergebene die Anforderungen der angegebenen erfüllt Funktionen. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- In der Standardeinstellung überschreiben dieser Methode sollten nicht löschen, die Inhalte von Objekten, die vom Benutzer ausgeblendet sind, es sei denn, die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Ein Fehler geschrieben werden soll, wenn Sie den Pfad ein Elements darstellt, die vom Benutzer ausgeblendet ist und [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) nastaven NA hodnotu `false`.

- Die Implementierung von der [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) Methodenaufruf sollten [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess* ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) und den Rückgabewert zu überprüfen, bevor Sie Änderungen an den Datenspeicher. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, wenn eine Änderung, mit dem Datenspeicher vorgenommen wird, z. B. das Löschen von Inhalt. Die [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) Methode sendet den Namen der Ressource, die für den Benutzer mit der Windows PowerShell-Laufzeit behandeln alle befehlszeileneinstellungen oder eine Einstellung geändert werden Variablen, bei der Bestimmung, was angezeigt werden soll.

  Nach dem Aufruf von [System.Management.Automation.Provider.Cmdletprovider.Shouldprocess*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt `true`, [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) Methodenaufruf sollte die [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) Methode. Diese Methode sendet eine Nachricht an den Benutzer können Sie Feedback zu überprüfen, ob der Vorgang fortgesetzt werden soll. Der Aufruf von [System.Management.Automation.Provider.Cmdletprovider.Shouldcontinue*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) ermöglicht eine zusätzliche Überprüfung auf potenziell gefährliche systemmodifizierungen.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Dynamische Parameter Anfügen an das Cmdlet Clear-Content

Die `Clear-Content` Cmdlet möglicherweise zusätzliche dynamische Parametern, die zur Laufzeit hinzugefügt werden. Um diese dynamischen Parameter zu gewährleisten, muss der Windows PowerShell-Inhaltsanbieter implementieren die [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) Methode, um diese zu verarbeiten Parameter. Diese Methode ruft die Parameter für das Element am angegebenen Pfad ab. Diese Methode ruft die dynamischen Parameter für das Element am angegebenen Pfad ab und gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [ System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, das Cmdlet den Parameter hinzu.

Diese Windows-PowerShell-Containeranbieter implementiert diese Methode nicht. Der folgende Code ist jedoch die Standardimplementierung dieser Methode.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L1819-L1822 "AccessDBProviderSample06.cs")]

## <a name="code-sample"></a>Codebeispiel

Vollständigen Beispielcode finden Sie unter [AccessDbProviderSample06 Codebeispiel](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Wenn Sie einen Anbieter schreiben, ist es möglicherweise notwendig, vorhandene Objekte hinzufügen oder neue Objekte zu definieren. Wenn dies abgeschlossen ist, müssen Sie erstellen eine Typendatei, die Windows PowerShell verwenden können, um der Member des Objekts zu identifizieren und einer Formatdatei, die definiert, wie das Objekt angezeigt wird. Weitere Informationen finden Sie unter [Objekttypen erweitern und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351).

## <a name="building-the-windows-powershell-provider"></a>Erstellen den Windows PowerShell-Anbieter

Finden Sie unter [so registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-windows-powershell-provider"></a>Testen der Windows PowerShell-Anbieter

Bei Ihrem Windows PowerShell-Anbieter mit Windows PowerShell registriert wurde, können Sie es testen, indem die unterstützten Cmdlets in der Befehlszeile ausgeführt. Z. B. testen Sie den Beispiel-Inhaltsanbieter aus.

Verwenden der `Get-Content` -Cmdlet zum Abrufen des Inhalts des angegebenen Elements in der Datenbanktabelle, an dem vom angegebenen Pfad die `Path` Parameter. Die `ReadCount` Parameter gibt die Anzahl der Elemente für den definierten Inhalt Reader zum Lesen (Standard: 1). Mit dem folgenden Befehlseintrag wird das Cmdlet ruft zwei Zeilen (Elemente) aus der Tabelle ab und deren Inhalt angezeigt. Beachten Sie, dass die Ausgabe des folgenden Beispiels eine fiktive Access-Datenbank verwendet.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```output
ID        : 1
FirstName : Eric
LastName  : Gruber
Email     : ericgruber@fabrikam.com
Title     : President
Company   : Fabrikam
WorkPhone : (425) 555-0100
Address   : 4567 Main Street
City      : Buffalo
State     : NY
Zip       : 98052
Country   : USA
ID        : 2
FirstName : Eva
LastName  : Corets
Email     : evacorets@cohowinery.com
Title     : Sales Representative
Company   : Coho Winery
WorkPhone : (360) 555-0100
Address   : 8910 Main Street
City      : Cabmerlot
State     : WA
Zip       : 98089
Country   : USA
```

## <a name="see-also"></a>Weitere Informationen

[Erstellen von Windows PowerShell-Anbieter](./how-to-create-a-windows-powershell-provider.md)

[Entwurf der Windows-PowerShell-Anbieter](./designing-your-windows-powershell-provider.md)

[Erweitern die Objekttypen und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Implementieren eines Navigation Windows PowerShell-Anbieters](./creating-a-windows-powershell-navigation-provider.md)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell Handbuch für Programmierer](./windows-powershell-programmer-s-guide.md)
