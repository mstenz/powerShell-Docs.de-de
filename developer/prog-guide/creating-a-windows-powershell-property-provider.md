---
title: Erstellen eines Anbieters der Windows PowerShell-Eigenschaft | Microsoft-Dokumentation
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
ms.openlocfilehash: 6ec0752a9ae06c5c2cdd1a1851caeeff52d8eb74
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081834"
---
# <a name="creating-a-windows-powershell-property-provider"></a>Erstellen eines Windows PowerShell-Eigenschaftenanbieters

Dieses Thema beschreibt, wie Sie einen Anbieter zu erstellen, der dem Benutzer ermöglicht, die die Eigenschaften von Elementen in einem Datenspeicher zu bearbeiten. Daher ist diese Art von Anbieter als ein Windows PowerShell-Eigenschaftenanbieter bezeichnet. Beispielsweise den Registrierungsanbieter vom Windows PowerShell-Handles Registrierungsschlüsselwerte als Eigenschaften der registrierungsschlüsselelements bereitgestellt. Diese Art von Anbieter muss hinzufügen, die [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) Schnittstelle, um die Implementierung der .NET-Klasse.

> [!NOTE]
> Windows PowerShell bietet eine Vorlagendatei, die Sie verwenden können, um ein Windows PowerShell-Anbieter zu entwickeln. Die Datei TemplateProvider.cs steht auf der Microsoft Windows Software Development Kit für Windows Vista und .NET Framework 3.0-Laufzeitkomponenten zur Verfügung. Anweisungen zum Herunterladen, finden Sie unter [das Installieren von Windows PowerShell und das Windows PowerShell-SDK-Download](/powershell/developer/installing-the-windows-powershell-sdk).
>
> Die heruntergeladene Vorlage, die die  **\<PowerShell-Beispiele >** Verzeichnis. Sie sollten eine Kopie dieser Datei und verwenden die Kopie für die Erstellung eines neuen Windows PowerShell-Anbieters, entfernen alle Funktionen, die Sie nicht benötigen.
>
> Weitere Informationen zu anderen Implementierungen der Windows PowerShell-Anbieter, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md).

> [!CAUTION]
> Die Methoden des Eigenschaftenanbieters sollten schreiben alle Objekte, die mit der [System.Management.Automation.Provider.Cmdletprovider.Writepropertyobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WritePropertyObject) Methode.

Die folgende Liste enthält die Abschnitte in diesem Thema. Wenn Sie für das Schreiben eines Eigenschaftenanbieters Windows PowerShell nicht vertraut sind, lesen Sie diese Informationen in der Reihenfolge, die er angezeigt wird. Aber wenn Sie für das Schreiben eines Eigenschaftenanbieters Windows PowerShell vertraut sind, wechseln Sie direkt auf die Informationen, die Sie benötigen.

- [Definieren den Windows PowerShell-Anbieter](#Defining-the-Windows-PowerShell-provider)

- [Definiert die grundlegenden Funktionen](#Defining-Base-Functionality)

- [Abrufen von Eigenschaften](#Retrieving-Properties)

- [Anfügen von dynamische Parametern zu der `Get-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Get-ItemProperty-Cmdlet)

- [Festlegen von Eigenschaften](#Setting-Properties)

- [Anfügen von dynamische Parametern zu der `Set-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-for-the-Set-ItemProperty-Cmdlet)

- [Löschen einer Eigenschaft](#Clearing-Properties)

- [Anfügen von dynamische Parametern zu der `Clear-ItemProperty` Cmdlet](#Attaching-Dynamic-Parameters-to-the-Clear-ItemProperty-Cmdlet)

- [Erstellen den Windows PowerShell-Anbieter](#Building-the-Windows-PowerShell-provider)

## <a name="defining-the-windows-powershell-provider"></a>Definieren den Windows PowerShell-Anbieter

Ein Eigenschaftenanbieter muss erstellen Sie eine .NET-Klasse, die unterstützt die [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) Schnittstelle. Hier ist die Standard-Klassendeklaration aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration](Msh_samplestestcmdlets#testcmdletspropertyproviderclassdeclaration)]  -->

## <a name="defining-base-functionality"></a>Definiert die grundlegenden Funktionen

Die [System.Management.Automation.Provider.Ipropertycmdletprovider](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider) Schnittstelle an die Anbieter-Basisklassen, angefügt werden kann, mit Ausnahme von der [ System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse. Fügen Sie die grundlegende Funktionen, die von der Basisklasse erforderlich ist, die Sie verwenden. Weitere Informationen zu Basisklassen finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md).

## <a name="retrieving-properties"></a>Abrufen von Eigenschaften

Zum Abrufen der Eigenschaften der Anbieter muss implementieren die [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) -Methode zur Unterstützung der Aufrufe von der `Get-ItemProperty` Cmdlet. Diese Methode ruft die Eigenschaften des Elements im angegebenen internen Anbieter-Pfad (voll qualifizierte) ab.

Die `providerSpecificPickList` Parameter gibt an, welche Eigenschaften abgerufen. Wenn dieser Parameter ist `null` oder leer ist, die Methode alle Eigenschaften abrufen soll. Darüber hinaus [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) schreibt eine Instanz von einem [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) Objekt, das darstellt ein der Eigenschaftenbehälter mit der abgerufenen Eigenschaften. Die Methode sollte nichts zurückgeben.

Es wird empfohlen, die Implementierung der [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) unterstützt die platzhaltererweiterung von Eigenschaftennamen für jedes Element in der Auswahlliste. Verwenden Sie hierzu die [System.Management.Automation.Wildcardpattern](/dotnet/api/System.Management.Automation.WildcardPattern) Klasse, um die Mustervergleich mit Platzhaltern auszuführen.

Hier ist die standardmäßige Implementierung des [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidergetproperty)]  -->

#### <a name="things-to-remember-about-implementing-getproperty"></a>Punkte zu beachten, die zur Implementierung der GetProperty

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-Eigenschaftenanbieter ExpandWildcards, Filter, einschließen oder ausschließen, die Funktionen des Anbieters deklarieren, aus der [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Ipropertycmdletprovider.Getproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetProperty) Methode muss sicherstellen, dass der Pfad, an die Methode übergeben, die Anforderungen des angegebenen entspricht Funktionen. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht abgerufen werden einen Reader für Objekte, die vom Benutzer ausgeblendet werden, es sei denn, die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Ein Fehler geschrieben werden soll, wenn Sie den Pfad ein Elements darstellt, die vom Benutzer ausgeblendet ist und [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) nastaven NA hodnotu `false`.

## <a name="attaching-dynamic-parameters-to-the-get-itemproperty-cmdlet"></a>Das Cmdlet "Get-ItemProperty" Anfügen dynamische Parameter

Die `Get-ItemProperty` Cmdlet möglicherweise zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Um diese dynamischen Parameter zu gewährleisten, muss der Anbieter der Windows PowerShell-Eigenschaft implementieren die [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) Methode. Die `path` Parameter gibt an, einen vollständig qualifizierten internen Anbieter-Pfad, während die `providerSpecificPickList` Parameter gibt an, die anbieterspezifische Eigenschaften, die in der Befehlszeile eingegeben. Dieser Parameter möglicherweise `null` oder leer sein, wenn die Eigenschaften an das Cmdlet geleitet werden. In diesem Fall gibt diese Methode ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die Windows PowerShell-Laufzeit verwendet das zurückgegebene Objekt, das Cmdlet den Parameter hinzu.

Hier ist die standardmäßige Implementierung des [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidergetpropertydynamicparameters)]  -->

## <a name="setting-properties"></a>Festlegen von Eigenschaften

Um Eigenschaften festzulegen, muss der Anbieter der Windows PowerShell-Eigenschaft implementieren die [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) -Methode zur Unterstützung der Aufrufe von der `Set-ItemProperty` Cmdlet. Diese Methode legt eine oder mehrere Eigenschaften des Elements am angegebenen Pfad fest, und die angegebenen Eigenschaften nach Bedarf überschrieben. [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) schreibt außerdem eine Instanz von einem [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) Objekt, das einen Eigenschaftenbehälter mit der aktualisierten darstellt. Eigenschaften.

Hier ist die standardmäßige Implementierung des [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty](Msh_samplestestcmdlets#testcmdletspropertyprovidersetproperty)]  -->

#### <a name="things-to-remember-about-implementing-set-itemproperty"></a>Punkte zu beachten, die zum Implementieren von Set-ItemProperty

Möglicherweise gelten die folgenden Bedingungen zu einer Implementierung von [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-Eigenschaftenanbieter ExpandWildcards, Filter, einschließen oder ausschließen, die Funktionen des Anbieters deklarieren, aus der [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) Methode muss sicherstellen, dass der Pfad, an die Methode übergebene die Anforderungen der angegebenen erfüllt Funktionen. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht abgerufen werden einen Reader für Objekte, die vom Benutzer ausgeblendet werden, es sei denn, die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Ein Fehler geschrieben werden soll, wenn Sie den Pfad ein Elements darstellt, die vom Benutzer ausgeblendet ist und [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) nastaven NA hodnotu `false`.

- Die Implementierung von der [System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) Methodenaufruf sollten [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) und den Rückgabewert zu überprüfen, bevor Sie Änderungen an den Datenspeicher. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, wenn ein Systemstatus, z. B. Änderung Umbenennen von Dateien. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sendet den Namen der Ressource, die geändert werden, um den Benutzer mit der Windows PowerShell-Laufzeit und Behandeln von Befehlszeilen-Einstellungen oder Preference-Variablen, bei der Ermittlung Was angezeigt werden soll.

  Nach dem Aufruf von [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt `true`, wenn gefährliche System Änderungen vorgenommen werden können, die [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetProperty) Methodenaufruf sollte die [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) Methode. Diese Methode sendet eine bestätigungsmeldung an den Benutzer können Sie zusätzliches Feedback, um anzugeben, dass der Vorgang fortgesetzt werden soll.

## <a name="attaching-dynamic-parameters-for-the-set-itemproperty-cmdlet"></a>Dynamische Parameter anfügen für das Cmdlet Set-ItemProperty

Die `Set-ItemProperty` Cmdlet möglicherweise zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Um diese dynamischen Parameter zu gewährleisten, muss der Anbieter der Windows PowerShell-Eigenschaft implementieren die [System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) Methode. Diese Methode gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die `null` Wert zurückgegeben werden kann, wenn es sind keine dynamischen Parameter hinzugefügt werden.

Hier ist die standardmäßige Implementierung des [System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyprovidersetpropertydynamicparameters)]  -->

## <a name="clearing-properties"></a>Löschen von Eigenschaften

Um Eigenschaften zu löschen, muss der Anbieter der Windows PowerShell-Eigenschaft implementieren die [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) -Methode zur Unterstützung der Aufrufe von der `Clear-ItemProperty` Cmdlet. Diese Methode legt eine oder mehrere Eigenschaften für das Element am angegebenen Pfad befindet.

Hier ist die standardmäßige Implementierung des [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty](Msh_samplestestcmdlets#testcmdletspropertyproviderclearproperty)]  -->

#### <a name="thing-to-remember-about-implementing-clearproperty"></a>Vergessen Sie nicht: zur Implementierung der ClearProperty

Die folgenden Bedingungen für Ihre Implementierung der gelten möglicherweise [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty):

- Wenn die Provider-Klasse zu definieren, kann ein Windows PowerShell-Eigenschaftenanbieter ExpandWildcards, Filter, einschließen oder ausschließen, die Funktionen des Anbieters deklarieren, aus der [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. In diesen Fällen die Implementierung der [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) Methode muss sicherstellen, dass der Pfad, an die Methode übergeben, die Anforderungen des angegebenen entspricht Funktionen. Zu diesem Zweck die Methode sollte Zugriff auf die entsprechende Eigenschaft, z. B. die [System.Management.Automation.Provider.Cmdletprovider.Exclude*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Exclude) und [ System.Management.Automation.Provider.Cmdletprovider.Include*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Include) Eigenschaften.

- Standardmäßig überschreibt diese Methode sollte nicht abgerufen werden einen Reader für Objekte, die vom Benutzer ausgeblendet werden, es sei denn, die [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) -Eigenschaftensatz auf `true`. Ein Fehler geschrieben werden soll, wenn Sie den Pfad ein Elements darstellt, die vom Benutzer ausgeblendet ist und [System.Management.Automation.Provider.Cmdletprovider.Force*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Force) nastaven NA hodnotu `false`.

- Die Implementierung von der [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) Methodenaufruf sollten [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess ](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) und den Rückgabewert zu überprüfen, bevor Sie Änderungen an den Datenspeicher. Diese Methode wird verwendet, um die Ausführung eines Vorgangs zu bestätigen, bevor eine Änderung vorgenommen wird, um den Systemstatus wie z. B. das Löschen von Inhalt. [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) sendet den Namen der Ressource, die für den Benutzer geändert werden, mit der Windows PowerShell-Laufzeit berücksichtigt alle über die befehlszeileneinstellungen oder der Preference-Variablen in bestimmen, was angezeigt werden soll.

  Nach dem Aufruf von [System.Management.Automation.Provider.Cmdletprovider.ShouldProcess](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldProcess) gibt `true`, wenn gefährliche System Änderungen vorgenommen werden können, die [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearproperty*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearProperty) Methodenaufruf sollte die [System.Management.Automation.Provider.Cmdletprovider.ShouldContinue](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.ShouldContinue) Methode. Diese Methode sendet eine bestätigungsmeldung an den Benutzer können Sie zusätzliches Feedback, um anzugeben, dass der gefährliche Vorgang fortgesetzt werden soll.

## <a name="attaching-dynamic-parameters-to-the-clear-itemproperty-cmdlet"></a>Dynamische Parameter Anfügen an das Cmdlet Clear-ItemProperty

Die `Clear-ItemProperty` Cmdlet möglicherweise zusätzliche Parameter, die dynamisch zur Laufzeit angegeben werden. Um diese dynamischen Parameter zu gewährleisten, muss der Anbieter der Windows PowerShell-Eigenschaft implementieren die [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) Methode. Diese Methode gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt. Die `null` Wert zurückgegeben werden kann, wenn es sind keine dynamischen Parameter hinzugefügt werden.

Hier ist die standardmäßige Implementierung des [System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) aus der TemplateProvider.cs-Datei, die von Windows PowerShell bereitgestellt.

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters](Msh_samplestestcmdlets#testcmdletspropertyproviderclearpropertydynamicparameters)]  -->

## <a name="building-the-windows-powershell-provider"></a>Erstellen den Windows PowerShell-Anbieter

Finden Sie unter [so registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md)

[Entwurf der Windows-PowerShell-Anbieter](./designing-your-windows-powershell-provider.md)

[Erweitern die Objekttypen und Formatierung](http://msdn.microsoft.com/en-us/da976d91-a3d6-44e8-affa-466b1e2bd351)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](http://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)