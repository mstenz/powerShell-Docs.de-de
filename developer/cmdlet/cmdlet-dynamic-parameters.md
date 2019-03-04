---
title: -Cmdlet dynamische Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8ae2196d-d6c8-4101-8805-4190d293af51
caps.latest.revision: 13
ms.openlocfilehash: 2fc73b6ef5a862fafb7a3c8fe3da19ac71bafc05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853806"
---
# <a name="cmdlet-dynamic-parameters"></a>Dynamische Cmdlet-Parameter

Cmdlets können Parameter definieren, die für den Benutzer unter speziellen Bedingungen, z. B. wenn das Argument eines anderen Parameters für einen bestimmten Wert ist verfügbar sind. Diese Parameter werden zur Laufzeit hinzugefügt und werden als bezeichnet *dynamische Parameter* , da sie nur bei Bedarf hinzugefügt werden. Beispielsweise können Sie ein Cmdlet entwerfen, die mehrere Parameter hinzufügt, nur, wenn Sie ein bestimmten Switch-Parameter angegeben wird.

> [!NOTE]
> Anbieter und Windows PowerShell-Funktionen können auch mit dynamische Parametern definieren.

## <a name="dynamic-parameters-in-windows-powershell-cmdlets"></a>Dynamische Parameter in Windows PowerShell-Cmdlets

Windows PowerShell verwendet dynamische Parameter in einige der Anbieter-Cmdlets. Z. B. die `Get-Item` und `Get-ChildItem` hinzufügen-Cmdlets eine `CodeSigningCert` Parameter zur Laufzeit bei der `Path` -Parameter des Cmdlets gibt den Pfad des Anbieters an. Wenn die `Path` -Parameter des Cmdlets gibt einen Pfad für einen anderen Anbieter, der `CodeSigningCert` Parameter ist nicht verfügbar.

Die folgenden Beispiele zeigen wie die `CodeSigningCert` -Parameter zur Laufzeit hinzugefügt bei der `Get-Item` Cmdlet ausgeführt wird.

Im ersten Beispiel ist die Windows PowerShell-Laufzeit wurde den Parameter hinzugefügt, und das Cmdlet erfolgreich ist.

```powershell
Get-Item -Path cert:\CurrentUser -codesigningcert
```

```output
Location   : CurrentUser
StoreNames : {SmartCardRoot, UserDS, AuthRoot, CA...}
```

Klicken Sie im zweiten Beispiel einem Dateisystemlaufwerk angegeben ist, und ein Fehler zurückgegeben. Die Fehlermeldung gibt an, dass die `CodeSigningCert` Parameter wurde nicht gefunden.

```powershell
Get-Item -Path C:\ -codesigningcert
```

```output
Get-Item : A parameter cannot be found that matches parameter name 'codesigningcert'.
At line:1 char:37
+  get-item -path C:\ -codesigningcert <<<<
--------
    CategoryInfo          : InvalidArgument: (:) [Get-Item], ParameterBindingException
    FullyQualifiedErrorId : NamedParameterNotFound,Microsoft.PowerShell.Commands.GetItemCommand
```

## <a name="support-for-dynamic-parameters"></a>Unterstützung für dynamische Parameter

Um dynamische Parameter zu unterstützen, muss der Cmdlet-Code die folgenden Elemente enthalten.

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters) diese Schnittstelle stellt die Methode, die dynamischen Parameter abruft.

Beispiel:

`public class SendGreetingCommand : Cmdlet, IDynamicParameters`

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters) diese Methode ruft das Objekt, das die Definitionen für die dynamischen Parameter enthält.

Beispiel:

```csharp
 public object GetDynamicParameters()
 {
   if (employee)
   {
     context= new SendGreetingCommandDynamicParameters();
     return context;
   }
   return null;
}
private SendGreetingCommandDynamicParameters context;
```

Dynamische Parameter-Klasse definiert diese Klasse die Parameter hinzugefügt werden. Diese Klasse muss einen Parameter-Attribut für jeden Parameter und alle optionalen Alias und Validierung-Attribute, die vom Cmdlet erforderlich sind, enthalten.

Beispiel:

```csharp
public class SendGreetingCommandDynamicParameters
{
  [Parameter]
  [ValidateSet ("Marketing", "Sales", "Development")]
  public string Department
  {
    get { return department; }
    set { department = value; }
  }
  private string department;
}
```

Ein vollständiges Beispiel eines Cmdlets, die dynamischen Parameter unterstützt, finden Sie unter [wie dynamische Parameter deklarieren](./how-to-declare-dynamic-parameters.md).

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.Idynamicparameters](/dotnet/api/System.Management.Automation.IDynamicParameters)

[System.Management.Automation.Idynamicparameters.Getdynamicparameters*](/dotnet/api/System.Management.Automation.IDynamicParameters.GetDynamicParameters)

[Gewusst wie: Deklarieren von dynamischen Parametern](./how-to-declare-dynamic-parameters.md)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
