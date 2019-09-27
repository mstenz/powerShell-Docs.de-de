---
title: Erstellen eines Windows PowerShell-Eigenschaften Anbieters | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- property providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], property provider
ms.assetid: a6adca44-b94b-4103-9970-a9b414355e60
caps.latest.revision: 5
ms.openlocfilehash: c36b93a5b4d3e7ef92d7f5b16381a8def2dd5466
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71323116"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Erstellen eines Windows PowerShell-Eigenschaftenanbieters

In diesem Thema wird beschrieben, wie Sie einen Anbieter erstellen, der es dem Benutzer ermöglicht, die Eigenschaften von Elementen in einem Datenspeicher zu bearbeiten. Daher wird dieser Anbietertyp als Windows PowerShell-Eigenschaften Anbieter bezeichnet. Der von Windows PowerShell bereitgestellte Registrierungs Anbieter verarbeitet z. b. Registrierungsschlüssel Werte als Eigenschaften des Registrierungsschlüssel Elements. Dieser Anbietertyp muss die [System. Management. Automation. Provider. ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) -Schnittstelle zur Implementierung der .NET-Klasse hinzufügen.

> [!NOTE]
> Windows PowerShell bietet eine Vorlagen Datei, die Sie zum Entwickeln eines Windows PowerShell-Anbieters verwenden können. Die Datei TemplateProvider.cs ist im Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3,0-Laufzeitkomponenten verfügbar. Anweisungen zum Herunterladen finden Sie unter [Installieren von Windows PowerShell und Herunterladen des Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladene Vorlage ist im Verzeichnis mit den  **\<PowerShell-Beispielen >** verfügbar. Erstellen Sie eine Kopie dieser Datei, und verwenden Sie die Kopie zum Erstellen eines neuen Windows PowerShell-Anbieters, um alle Funktionen zu entfernen, die Sie nicht benötigen.
>
> Weitere Informationen zu anderen Windows PowerShell-Anbieter Implementierungen finden [Sie unter Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Die Methoden des Eigenschaften Anbieters sollten alle-Objekte mithilfe der [System. Management. Automation. Provider. cmdletprovider. Write tepropertyobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) -Methode schreiben.

## <a name="defining-the-windows-powershell-provider"></a>Definieren des Windows PowerShell-Anbieters

Ein Eigenschaften Anbieter muss eine .NET-Klasse erstellen, die die [System. Management. Automation. Provider. ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) -Schnittstelle unterstützt. Hier ist die Standardklassen Deklaration aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt wird.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definieren der Basisfunktionalität

Die [System. Management. Automation. Provider. ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) -Schnittstelle kann mit Ausnahme der [System. Management. Automation. Provider. drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) -Klasse an jede der Anbieter Basisklassen angefügt werden. Fügen Sie die Basisfunktionen hinzu, die für die von Ihnen verwendete Basisklasse erforderlich sind. Weitere Informationen zu Basisklassen finden Sie unter [Entwerfen des Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Abrufen von Eigenschaften

Zum Abrufen von Eigenschaften muss der Anbieter die [System. Management. Automation. Provider. ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) -Methode implementieren, um Aufrufe aus `Get-ItemProperty` dem Cmdlet zu unterstützen. Diese Methode ruft die Eigenschaften des Elements ab, das sich am angegebenen Anbieter internen Pfad (voll qualifiziert) befindet.

Der `providerSpecificPickList` -Parameter gibt an, welche Eigenschaften abgerufen werden sollen. Wenn dieser Parameter oder `null` leer ist, sollte die Methode alle Eigenschaften abrufen. Außerdem wird von [System. Management. Automation. Provider. ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) eine Instanz eines [System. Management. Automation. psobject](/dotnet/api/System.Management.Automation.PSObject) -Objekts geschrieben, das einen Eigenschaften Behälter der abgerufenen Eigenschaften darstellt. Die Methode sollte nichts zurückgeben.

Es wird empfohlen, dass die Implementierung von [System. Management. Automation. Provider. ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) die Platzhalter Erweiterung von Eigenschaftsnamen für jedes Element in der Auswahlliste unterstützt. Verwenden Sie hierzu die [System. Management. Automation. wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) -Klasse, um den Platzhalter Musterabgleich auszuführen.

Dies ist die Standard Implementierung von [System. Management. Automation. Provider. ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt wird.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Dinge, die Sie beim Implementieren von GetProperty beachten sollten

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty)gelten:

- Beim Definieren der Anbieter Klasse kann ein Windows PowerShell-Eigenschaften Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. ipropertycmdletprovider. GetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) -Methode sicherstellen, dass der Pfad, der an die-Methode übergeben wird, die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode keinen Reader für Objekte abrufen, die für den Benutzer ausgeblendet sind, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft `true`ist auf festgelegt. Ein Fehler sollte geschrieben werden, wenn der Pfad ein Element darstellt, das für den Benutzer ausgeblendet ist, und [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ist auf `false`festgelegt.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Anfügen dynamischer Parameter an das Cmdlet "Get-ItemProperty"

Das `Get-ItemProperty` Cmdlet erfordert möglicherweise zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Eigenschaften Anbieter die [System. Management. Automation. Provider. ipropertycmdletprovider. getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) -Methode implementieren. Der `path` -Parameter gibt einen voll qualifizierten Anbieter internen Pfad an, während der `providerSpecificPickList` -Parameter die anbieterspezifischen Eigenschaften angibt, die in der Befehlszeile eingegeben werden. Dieser Parameter kann oder `null` leer sein, wenn die Eigenschaften an das Cmdlet weitergeleitet werden. In diesem Fall gibt diese Methode ein Objekt zurück, das Eigenschaften und Felder mit Eigenschaften und Feldern hat, ähnlich wie eine Cmdlet-Klasse oder ein [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene-Objekt, um die Parameter zum Cmdlet hinzuzufügen.

Dies ist die Standard Implementierung von [System. Management. Automation. Provider. ipropertycmdletprovider. getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt wird.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Festlegen von Eigenschaften

Zum Festlegen von Eigenschaften muss der Windows PowerShell-Eigenschaften Anbieter die [System. Management. Automation. Provider. ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) -Methode implementieren, um Aufrufe `Set-ItemProperty` aus dem Cmdlet zu unterstützen. Diese Methode legt eine oder mehrere Eigenschaften des Elements im angegebenen Pfad fest und überschreibt die angegebenen Eigenschaften nach Bedarf. [System. Management. Automation. Provider. ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) schreibt außerdem eine Instanz eines [System. Management. Automation. psobject](/dotnet/api/System.Management.Automation.PSObject) -Objekts, das einen Eigenschaften Behälter der aktualisierten Eigenschaften darstellt.

Dies ist die Standard Implementierung von [System. Management. Automation. Provider. ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt wird.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Dinge, die Sie beim Implementieren von Set-ItemProperty beachten sollten

Die folgenden Bedingungen können auf eine Implementierung von [System. Management. Automation. Provider. ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty)zutreffen:

- Beim Definieren der Anbieter Klasse kann ein Windows PowerShell-Eigenschaften Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) -Methode sicherstellen, dass der Pfad, der an die-Methode übergeben wird, die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode keinen Reader für Objekte abrufen, die für den Benutzer ausgeblendet sind, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft `true`ist auf festgelegt. Ein Fehler sollte geschrieben werden, wenn der Pfad ein Element darstellt, das für den Benutzer ausgeblendet ist, und [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ist auf `false`festgelegt.

- Ihre Implementierung der [System. Management. Automation. Provider. ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) -Methode sollte [System. Management. Automation. Provider. cmdletprovider. schuldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aufrufen und ihren Rückgabewert überprüfen. vor dem vornehmen von Änderungen am Datenspeicher. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, wenn eine Änderung am Systemstatus vorgenommen wird, z. b. beim Umbenennen von Dateien. [System. Management. Automation. Provider. cmdletprovider. tiondprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sendet den Namen der Ressource, die mit der Windows PowerShell-Laufzeit an den Benutzer geändert werden soll, und verarbeitet alle Befehlszeilen Einstellungen oder Einstellungs Variablen, um zu bestimmen, was sollte angezeigt werden.

  Nach der Rückgabe des Aufrufes von [System. Management. Automation. Provider. cmdletprovider. dauerdprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt `true`, wenn potenziell gefährliche System Änderungen vorgenommen werden können, die [ Die System. Management. Automation. Provider. ipropertycmdletprovider. SetProperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) -Methode muss die [System. Management. Automation. Provider. cmdletprovider. schuldcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Methode aufrufen. Diese Methode sendet eine Bestätigungsmeldung an den Benutzer, damit zusätzliches Feedback angezeigt werden kann, um anzugeben, dass der Vorgang fortgesetzt werden soll.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Anfügen dynamischer Parameter für das Set-ItemProperty-Cmdlet

Das `Set-ItemProperty` Cmdlet erfordert möglicherweise zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Eigenschaften Anbieter die [System. Management. Automation. Provider. ipropertycmdletprovider. setpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) -Methode implementieren. Diese Methode gibt ein Objekt zurück, das über Eigenschaften und Felder mit Attribut Attributen verfügt, die einer Cmdlet-Klasse oder einem [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt ähneln. Der `null` Wert kann zurückgegeben werden, wenn keine dynamischen Parameter hinzugefügt werden sollen.

Dies ist die Standard Implementierung von [System. Management. Automation. Provider. ipropertycmdletprovider. getpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt wird.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Löschen von Eigenschaften

Zum Löschen von Eigenschaften muss der Windows PowerShell-Eigenschaften Anbieter die [System. Management. Automation. Provider. ipropertycmdletprovider. clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) -Methode implementieren, um Aufrufe `Clear-ItemProperty` aus dem Cmdlet zu unterstützen. Diese Methode legt eine oder mehrere Eigenschaften für das Element fest, das sich im angegebenen Pfad befindet.

Dies ist die Standard Implementierung von [System. Management. Automation. Provider. ipropertycmdletprovider. clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt wird.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Beachten Sie, dass clearproperty nicht implementiert werden muss.

Die folgenden Bedingungen können für Ihre Implementierung von [System. Management. Automation. Provider. ipropertycmdletprovider. clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty)gelten:

- Beim Definieren der Anbieter Klasse kann ein Windows PowerShell-Eigenschaften Anbieter die Anbieter Funktionen von expandwildcards, Filtern, einschließen oder Ausschließen von der [System. Management. Automation. Provider. providerfunktionalitäten](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) -Enumeration deklarieren. In diesen Fällen muss die Implementierung der [System. Management. Automation. Provider. ipropertycmdletprovider. clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) -Methode sicherstellen, dass der an die Methode übergebenen Pfad die Anforderungen der angegebenen Funktionen erfüllt. Zu diesem Zweck sollte die-Methode auf die entsprechende Eigenschaft zugreifen, z. b. die [System. Management. Automation. Provider. cmdletprovider. Exclude *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) -und [System. Management. Automation. Provider. cmdletprovider. include *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) -Eigenschaften.

- Standardmäßig sollten über schreibungen dieser Methode keinen Reader für Objekte abrufen, die für den Benutzer ausgeblendet sind, es sei denn, die [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaft `true`ist auf festgelegt. Ein Fehler sollte geschrieben werden, wenn der Pfad ein Element darstellt, das für den Benutzer ausgeblendet ist, und [System. Management. Automation. Provider. cmdletprovider. Force *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) ist auf `false`festgelegt.

- Ihre Implementierung der [System. Management. Automation. Provider. ipropertycmdletprovider. clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) -Methode sollte [System. Management. Automation. Provider. cmdletprovider. schuldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) aufrufen und deren Rückgabewert überprüfen. vor dem vornehmen von Änderungen am Datenspeicher. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, bevor eine Änderung am Systemstatus vorgenommen wird, z. b. das Löschen von Inhalt. [System. Management. Automation. Provider. cmdletprovider. schuldprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sendet den Namen der Ressource, die an den Benutzer geändert werden soll, wobei die Windows PowerShell-Laufzeit alle Befehlszeilen Einstellungen oder Einstellungs Variablen beim Bestimmen von Was angezeigt werden soll.

  Nach der Rückgabe des Aufrufes von [System. Management. Automation. Provider. cmdletprovider. dauerdprocess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt `true`, wenn potenziell gefährliche System Änderungen vorgenommen werden können, die [ Die System. Management. Automation. Provider. ipropertycmdletprovider. clearproperty *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) -Methode muss die [System. Management. Automation. Provider. cmdletprovider. schuldcontinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) -Methode aufrufen. Diese Methode sendet eine Bestätigungsmeldung an den Benutzer, damit zusätzliches Feedback angezeigt werden kann, um anzugeben, dass der potenziell gefährliche Vorgang fortgesetzt werden soll.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Anfügen dynamischer Parameter an das Clear-ItemProperty-Cmdlet

Das `Clear-ItemProperty` Cmdlet erfordert möglicherweise zusätzliche Parameter, die zur Laufzeit dynamisch angegeben werden. Um diese dynamischen Parameter bereitzustellen, muss der Windows PowerShell-Eigenschaften Anbieter die [System. Management. Automation. Provider. ipropertycmdletprovider. clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) -Methode implementieren. Diese Methode gibt ein Objekt zurück, das über Eigenschaften und Felder mit Attribut Attributen verfügt, die einer Cmdlet-Klasse oder einem [System. Management. Automation. runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) -Objekt ähneln. Der `null` Wert kann zurückgegeben werden, wenn keine dynamischen Parameter hinzugefügt werden sollen.

Dies ist die Standard Implementierung von [System. Management. Automation. Provider. ipropertycmdletprovider. clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt wird.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Entwickeln des Windows PowerShell-Anbieters

Weitere Informationen finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Siehe auch

[Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md)

[Entwerfen Ihres Windows PowerShell-Anbieters](./designing-your-windows-powershell-provider.md)

[Erweitern von Objekttypen und Formatierung](https://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)