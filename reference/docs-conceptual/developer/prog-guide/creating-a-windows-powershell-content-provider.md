---
title: Erstellen eines Windows PowerShell-Inhaltsanbieters
ms.date: 09/13/2016
ms.topic: article
ms.assetid: 3da88ff9-c4c7-4ace-aa24-0a29c8cfa060
ms.openlocfilehash: e7a59d902633a6d4c73236b7f5a10fc4b405c9bf
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978473"
---
# <a name="creating-a-windows-powershell-content-provider"></a>Erstellen eines Windows PowerShell-Inhaltsanbieters

In diesem Thema wird beschrieben, wie Sie einen Windows PowerShell-Anbieter erstellen, der es dem Benutzer ermöglicht, den Inhalt der Elemente in einem Datenspeicher zu bearbeiten. Folglich wird ein Anbieter, der den Inhalt von Elementen bearbeiten kann, als Windows PowerShell-Inhaltsanbieter bezeichnet.

> [!NOTE]
> Sie können die C# Quelldatei (AccessDBSampleProvider06.cs) für diesen Anbieter mithilfe des Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3,0-Laufzeitkomponenten herunterladen. Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/scripting/developer/installing-the-windows-powershell-sdk).
> Die heruntergeladenen Quelldateien stehen im **\<PowerShell-Beispiele >** Verzeichnis zur Verfügung. Weitere Informationen zu anderen Windows PowerShell-Anbieter Implementierungen finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md).

## <a name="define-the-windows-powershell-content-provider-class"></a>Definieren der Windows PowerShell-Inhaltsanbieter Klasse

Ein Windows PowerShell-Inhaltsanbieter muss eine .NET-Klasse erstellen, die die [System. Management. Automation. Provider. icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -Schnittstelle unterstützt. Hier ist die Klassendefinition für den in diesem Abschnitt beschriebenen Element Anbieter.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="32-33":::

Beachten Sie, dass das [System. Management. Automation. Provider. cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) -Attribut in dieser Klassendefinition zwei Parameter enthält. Der erste Parameter gibt einen benutzerfreundlichen Namen für den Anbieter an, der von Windows PowerShell verwendet wird. Der zweite Parameter gibt die Windows PowerShell-spezifischen Funktionen an, die der Anbieter während der Befehls Verarbeitung für die Windows PowerShell-Laufzeit verfügbar macht. Für diesen Anbieter gibt es keine zusätzlichen Windows PowerShell-spezifischen Funktionen.

## <a name="define-functionality-of-base-class"></a>Definieren von Funktionen der Basisklasse

Wie unter [Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md)beschrieben, wird die [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Klasse von mehreren anderen Klassen abgeleitet, die unterschiedliche Anbieter Funktionen bereitgestellt haben. Daher definiert ein Windows PowerShell-Inhaltsanbieter in der Regel die gesamte Funktionalität, die von diesen Klassen bereitgestellt wird.

Weitere Informationen zum Implementieren von Funktionen zum Hinzufügen von Sitzungs spezifischen Initialisierungs Informationen und zum Freigeben von Ressourcen, die vom Anbieter verwendet werden, finden Sie unter [Erstellen eines einfachen Windows PowerShell-Anbieters](./creating-a-basic-windows-powershell-provider.md).
Die meisten Anbieter, einschließlich des hier beschriebenen Anbieters, können jedoch die Standard Implementierung dieser Funktionalität verwenden, die von Windows PowerShell bereitgestellt wird.

Der Anbieter muss die Methoden der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Basisklasse implementieren, um auf den Datenspeicher zugreifen zu können. Weitere Informationen zum Implementieren dieser Methoden finden Sie unter [Erstellen eines Windows PowerShell-Laufwerks Anbieters](./creating-a-windows-powershell-drive-provider.md).

Zum Bearbeiten der Elemente eines Datenspeicher, z. b. zum erhalten, festlegen und Löschen von Elementen, muss der Anbieter die von der [System. Management. Automation. Provider. itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) -Basisklasse bereitgestellten Methoden implementieren. Weitere Informationen zum Implementieren dieser Methoden finden Sie unter [Erstellen eines Windows PowerShell-Element Anbieters](./creating-a-windows-powershell-item-provider.md).

Der Anbieter muss die von der [System. Management. Automation. Provider. containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) -Basisklasse bereitgestellten Methoden implementieren, um an Daten speichern mit mehreren Ebenen arbeiten zu können. Weitere Informationen zum Implementieren dieser Methoden finden Sie unter [Erstellen eines Windows PowerShell-Container Anbieters](./creating-a-windows-powershell-container-provider.md).

Der Anbieter muss die [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Basisklasse implementieren, um rekursive Befehle, unterstützte Container und relative Pfade zu unterstützen. Außerdem kann dieser Windows PowerShell-Inhaltsanbieter die [System. Management. Automation. Provider. icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) -Schnittstelle an die [System. Management. Automation. Provider. navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) -Basisklasse anfügen und daher die von dieser Klasse bereitgestellten Methoden implementieren. Weitere Informationen finden Sie unter [Implementieren von Windows PowerShell-Navigations Anbietern in Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md).

## <a name="implementing-a-content-reader"></a>Implementieren eines Inhalts Readers

Zum Lesen von Inhalten aus einem Element muss ein Anbieter eine Inhalts Leser Klasse implementieren, die von [System. Management. Automation. Provider. icontentreader](/dotnet/api/System.Management.Automation.Provider.IContentReader)abgeleitet ist.
Der Inhalts Leser für diesen Anbieter ermöglicht den Zugriff auf den Inhalt einer Zeile in einer Datentabelle. Die Content Reader-Klasse definiert eine **Read** -Methode, die die Daten aus der festgelegten Zeile abruft und eine Liste zurückgibt, die diese Daten darstellt, eine **Seek** -Methode, die den Inhalts Reader verschiebt, eine **Close** -Methode, die den Inhalts Reader schließt, **und eine verwerfen** -Methode.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="2115-2241":::

## <a name="implementing-a-content-writer"></a>Implementieren eines inhaltswriter

Um Inhalt in ein Element zu schreiben, muss ein Anbieter eine inhaltswriter-Klasse implementieren, die von [System. Management. Automation. Provider. icontentwriter](/dotnet/api/System.Management.Automation.Provider.IContentWriter)abgeleitet ist.
Die inhaltswriter-Klasse definiert eine **Write** -Methode, die den angegebenen Zeilen Inhalt schreibt, eine **Seek** -Methode, die den inhaltswriter verschiebt, eine **Close** -Methode, die den inhaltswriter schließt, **und eine verwerfen** -Methode.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="2250-2394":::

## <a name="retrieving-the-content-reader"></a>Abrufen des Inhalts Readers

Um Inhalt von einem Element zu erhalten, muss der Anbieter [System. Management. Automation. Provider. icontentcmdletprovider. getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) implementieren, um das Cmdlet "`Get-Content`" zu unterstützen. Diese Methode gibt den Inhalts Leser für das Element zurück, das sich am angegebenen Pfad befindet. Das Reader-Objekt kann dann geöffnet werden, um den Inhalt zu lesen.

Hier ist die Implementierung von [System. Management. Automation. Provider. icontentcmdletprovider. getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) für diese Methode für diesen Anbieter.

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1829-1846":::

#### <a name="things-to-remember-about-implementing-getcontentreader"></a>Dinge, die Sie beim Implementieren von getcontentreader beachten sollten

Die folgenden Bedingungen können auf eine Implementierung von [System. Management. Automation. Provider. icontentcmdletprovider. getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader)zutreffen:

- Beim Definieren der Anbieter Klasse kann ein Windows PowerShell-Inhaltsanbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. icontentcmdletprovider. getcontentreader *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) -Methode sicherstellen, dass der Pfad, der an die-Methode übergeben wird, die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode keinen Reader für Objekte abrufen, die für den Benutzer ausgeblendet sind, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist auf `true`festgelegt. Ein Fehler sollte geschrieben werden, wenn der Pfad ein Element darstellt, das für den Benutzer ausgeblendet ist, und [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ist auf `false`festgelegt.

## <a name="attaching-dynamic-parameters-to-the-get-content-cmdlet"></a>Anfügen dynamischer Parameter an das Cmdlet "Get-Content"

Das Cmdlet "`Get-Content`" erfordert möglicherweise zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Inhaltsanbieter die [System. Management. Automation. Provider. icontentcmdletprovider. getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) -Methode implementieren. Diese Methode ruft dynamische Parameter für das Element an dem angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit ähnlichen Attributen wie eine Cmdlet-Klasse oder ein [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt verfügt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter zum Cmdlet hinzuzufügen.

Diese Methode wird von diesem Windows PowerShell-Container Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

```csharp
public object GetContentReaderDynamicParameters(string path)
{
    return null;
}
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1853-1856":::

## <a name="retrieving-the-content-writer"></a>Der inhaltswriter wird abgerufen.

Um Inhalt in ein Element zu schreiben, muss der Anbieter [System. Management. Automation. Provider. icontentcmdletprovider. getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) implementieren, um die Cmdlets "`Set-Content`" und "`Add-Content`" zu unterstützen. Diese Methode gibt den inhaltswriter für das Element zurück, das sich am angegebenen Pfad befindet.

Hier ist die Implementierung von [System. Management. Automation. Provider. icontentcmdletprovider. getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) für diese Methode.

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

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1863-1880":::

#### <a name="things-to-remember-about-implementing-getcontentwriter"></a>Dinge, die Sie beim Implementieren von getcontentwriter beachten sollten

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. icontentcmdletprovider. getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter)gelten:

- Beim Definieren der Anbieter Klasse kann ein Windows PowerShell-Inhaltsanbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. icontentcmdletprovider. getcontentwriter *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriter) -Methode sicherstellen, dass der Pfad, der an die-Methode übergeben wird, die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode keinen Writer für Objekte abrufen, die für den Benutzer ausgeblendet sind, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist auf `true`festgelegt. Ein Fehler sollte geschrieben werden, wenn der Pfad ein Element darstellt, das für den Benutzer ausgeblendet ist, und [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ist auf `false`festgelegt.

## <a name="attaching-dynamic-parameters-to-the-add-content-and-set-content-cmdlets"></a>Anfügen dynamischer Parameter an die Cmdlets "Add-Content" und "Set-Content"

Die `Add-Content`-und `Set-Content`-Cmdlets erfordern möglicherweise zusätzliche dynamische Parameter, die zur Laufzeit hinzugefügt werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Inhaltsanbieter die [System. Management. Automation. Provider. icontentcmdletprovider. getcontentschreiterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) -Methode implementieren, um diese Parameter zu verarbeiten. Diese Methode ruft dynamische Parameter für das Element an dem angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit ähnlichen Attributen wie eine Cmdlet-Klasse oder ein [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt verfügt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter den Cmdlets hinzuzufügen.

Diese Methode wird von diesem Windows PowerShell-Container Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1887-1890":::

## <a name="clearing-content"></a>Löschen von Inhalt

Ihr Inhaltsanbieter implementiert die [System. Management. Automation. Provider. icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) -Methode zur Unterstützung des `Clear-Content`-Cmdlets. Mit dieser Methode wird der Inhalt des Elements am angegebenen Pfad entfernt, das Element bleibt jedoch intakt.

Hier ist die Implementierung der [System. Management. Automation. Provider. icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) -Methode für diesen Anbieter.

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1775-1812":::

#### <a name="things-to-remember-about-implementing-clearcontent"></a>Dinge, die Sie beim Implementieren von ClearContent beachten sollten

Die folgenden Bedingungen können auf eine Implementierung von [System. Management. Automation. Provider. icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent)zutreffen:

- Beim Definieren der Anbieter Klasse kann ein Windows PowerShell-Inhaltsanbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) -Methode sicherstellen, dass der an die Methode übergebenen Pfad die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode nicht den Inhalt von Objekten löschen, die für den Benutzer ausgeblendet sind, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft ist auf `true`festgelegt. Ein Fehler sollte geschrieben werden, wenn der Pfad ein Element darstellt, das für den Benutzer ausgeblendet ist, und [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ist auf `false`festgelegt.

- Ihre Implementierung der [System. Management. Automation. Provider. icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) -Methode sollte [System. Management. Automation. Provider. cmdletprovider. schuldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aufrufen und den Rückgabewert überprüfen, bevor Änderungen am Datenspeicher vorgenommen werden. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, wenn eine Änderung am Datenspeicher vorgenommen wird, z. b. das Löschen von Inhalt. Die [System. Management. Automation. Provider. cmdletprovider. tiondprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) -Methode sendet den Namen der Ressource, die an den Benutzer geändert werden soll, und die Windows PowerShell-Laufzeit verarbeitet alle Befehlszeilen Einstellungen oder Einstellungs Variablen, um zu bestimmen, was angezeigt werden soll.

  Nach dem Aufrufen von [System. Management. Automation. Provider. cmdletprovider. schuldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) wird `true`zurückgegeben. die [System. Management. Automation. Provider. icontentcmdletprovider. ClearContent *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) -Methode sollte die [System. Management. Automation. Provider. cmdletprovider. dendcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Methode aufrufen. Diese Methode sendet eine Meldung an den Benutzer, damit das Feedback überprüft werden kann, ob der Vorgang fortgesetzt werden soll. Der [System. Management. Automation. Provider. cmdletprovider. rudcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Befehl ermöglicht eine zusätzliche Überprüfung auf potenziell gefährliche System Änderungen.

## <a name="attaching-dynamic-parameters-to-the-clear-content-cmdlet"></a>Anfügen dynamischer Parameter an das Cmdlet "Clear-Content"

Das Cmdlet "`Clear-Content`" erfordert möglicherweise zusätzliche dynamische Parameter, die zur Laufzeit hinzugefügt werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Inhaltsanbieter die [System. Management. Automation. Provider. icontentcmdletprovider. clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) -Methode implementieren, um diese Parameter zu verarbeiten. Diese Methode ruft die Parameter für das Element am angegeben Pfad ab. Diese Methode ruft dynamische Parameter für das Element an dem angezeigten Pfad ab und gibt ein Objekt zurück, das über Eigenschaften und Felder mit ähnlichen Attributen wie eine Cmdlet-Klasse oder ein [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt verfügt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter zum Cmdlet hinzuzufügen.

Diese Methode wird von diesem Windows PowerShell-Container Anbieter nicht implementiert. Der folgende Code ist jedoch die Standard Implementierung dieser Methode.

```csharp
public object ClearContentDynamicParameters(string path)
{
    return null;
}
```

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs" range="1819-1822":::

## <a name="code-sample"></a>Codebeispiel

Einen umfassenden Beispielcode finden Sie unter [AccessDbProviderSample06-Codebeispiel](./accessdbprovidersample06-code-sample.md).

## <a name="defining-object-types-and-formatting"></a>Definieren von Objekttypen und Formatierung

Beim Schreiben eines Anbieters müssen möglicherweise Elemente zu vorhandenen Objekten hinzugefügt oder neue Objekte definiert werden. Wenn dies geschehen ist, müssen Sie eine Typdatei erstellen, die Windows PowerShell verwenden kann, um die Member des Objekts und eine Format Datei zu identifizieren, die definiert, wie das Objekt angezeigt wird. Weitere Informationen finden Sie unter [Erweitern von Objekttypen und Formatierung](/previous-versions/ms714665(v=vs.85)).

## <a name="building-the-windows-powershell-provider"></a>Entwickeln des Windows PowerShell-Anbieters

Weitere Informationen finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions/ms714644(v=vs.85)).

## <a name="testing-the-windows-powershell-provider"></a>Testen des Windows PowerShell-Anbieters

Wenn Ihr Windows PowerShell-Anbieter bei Windows PowerShell registriert wurde, können Sie ihn testen, indem Sie die unterstützten Cmdlets in der Befehlszeile ausführen. Testen Sie z. b. den Beispiel Inhaltsanbieter.

Verwenden Sie das Cmdlet "`Get-Content`", um den Inhalt des angegebenen Elements in der Datenbanktabelle in dem Pfad abzurufen, der durch den `Path`-Parameter angegeben wird. Der `ReadCount`-Parameter gibt die Anzahl der Elemente an, die der definierte Inhalts Leser lesen soll (Standardwert: 1). Mit dem folgenden Befehls Eintrag Ruft das Cmdlet zwei Zeilen (Elemente) aus der Tabelle ab und zeigt ihren Inhalt an. Beachten Sie, dass die folgende Beispielausgabe eine fiktive Access-Datenbank verwendet.

```powershell
Get-Content -Path mydb:\Customers -ReadCount 2
```

```Output
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

[Erstellen von Windows PowerShell-Anbietern](./how-to-create-a-windows-powershell-provider.md)

[Entwerfen Ihres Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md)

[Erweitern von Objekttypen und Formatierung](/previous-versions//ms714665(v=vs.85))

[Implementieren eines Windows PowerShell-navigationsanbieters](./creating-a-windows-powershell-navigation-provider.md)

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions/ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Windows PowerShell-Programmier Handbuch](./windows-powershell-programmer-s-guide.md)
