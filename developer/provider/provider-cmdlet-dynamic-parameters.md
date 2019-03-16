---
title: Dynamische Parameter für Anbieter-Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058231"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Dynamische Anbieter-Cmdlet-Parameter

Anbieter können dynamische Parameter definieren, die einem Anbieter-Cmdlet hinzugefügt werden, wenn der Benutzer einen bestimmten Wert für eine der statischen Parameter des Cmdlets angibt. Z. B. kann einen Anbieter hinzuzufügen verschiedene dynamische Parameter, die basierend auf welchem Weg der Benutzer gibt an, wenn sie Aufrufen der `Get-Item` oder `Set-Item` Anbieter-Cmdlets.

## <a name="dynamic-parameter-methods"></a>Dynamischer Parameter-Methoden

Dynamische Parameter werden durch die Implementierung einer der Methoden dynamischer Parameter, wie z. B. definiert der [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) und [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s-Methoden. Diese Methoden geben ein Objekt mit öffentlichen Eigenschaften, die mit Attributen ähnelt derjenigen der eigenständigen Cmdlets ergänzt werden zurück. Hier ist ein Beispiel für die Implementierung von der [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) Methode der Zertifikatanbieter entnommen:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

Im Gegensatz zu den statischen Parameter des Anbieter-Cmdlets können Sie die Merkmale dieser Parameter auf die gleiche Weise angeben, dass in eigenständigen Cmdlets Parameter definiert sind. Hier ist ein Beispiel einer dynamischen Parameter-Klasse, die der Zertifikatanbieter entnommen:

```csharp
internal sealed class CertificateProviderDynamicParameters
{
  /// <summary>
  /// Dynamic parameter the controls whether we only return
  /// code signing certs.
  /// </summary>
  [Parameter()]
  public SwitchParameter CodeSigningCert
  {
    get
    {
      {
        return codeSigningCert;
      }
    }

    set
    {
      {
        codeSigningCert = value;
      }
    }
  }

    private SwitchParameter codeSigningCert = new SwitchParameter();
}
```

## <a name="dynamic-parameters"></a>Dynamische Parameter

Hier ist eine Liste der statischen Parameter, die zum Hinzufügen von dynamischen Parametern verwendet werden kann.

`Clear-Content` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` -Parameter des Cmdlets "Clear-Clear" durch die Implementierung der [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontentdynamicparameters* ](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) Methode.

`Clear-Item` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` Parameter der `Clear-Item` Cmdlet, durch die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Clearitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) Methode.

`Clear-ItemProperty` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` Parameter der `Clear-ItemProperty` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Ipropertycmdletprovider.Clearpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) Methode.

`Copy-Item` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path`, `Destination`, und `Recurse` Parameter von der `Copy-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Containercmdletprovider.Copyitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) Methode.

Cmdlet "Get-ChildItems" können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` und `Recurse` Parameter von der `Get-ChildItem` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Containercmdletprovider.Getchilditemsdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) und [System.Management.Automation.Provider.Containercmdletprovider.Getchildnamesdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) Methoden.

`Get-Content` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` Parameter der `Get-Content` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreaderdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) Methode.

`Get-Item` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` Parameter der `Get-Item` Cmdlet, durch die Implementierung der [System.Management.Automation.Provider.Itemcmdletprovider.Getitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) Methode.

`Get-ItemProperty` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` und `Name` Parameter von der `Get-ItemProperty` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Ipropertycmdletprovider.Getpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters) Methode.

`Invoke-Item` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` Parameter der `Invoke-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) Methode.

`Move-Item` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` und `Destination` Parameter von der `Move-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Navigationcmdletprovider.Moveitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters) Methode.

`New-Item` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path`, `ItemType`, und `Value` Parameter von der `New-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Containercmdletprovider.Newitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) Methode.

`New-ItemProperty` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path`, `Name`, `PropertyType`, und `Value` Parameter von der `New-ItemProperty` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Newpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) Methode.

`New-PSDrive` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die [: System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) zurückgegebenes Objekt der `New-PSDrive` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) Methode.

`Remove-Item` Sie können definieren, dass dynamische Parameter, die ausgelöst werden die `Path` und `Recurse` Parameter von der `Remove-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Containercmdletprovider.Removeitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) Methode.

`Remove-ItemProperty` Sie können definieren, dass dynamische Parameter, die ausgelöst werden die `Path` und `Name` Parameter von der `Remove-ItemProperty` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Removepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) Methode.

`Rename-Item` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` und `NewName` Parameter von der `Rename-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Containercmdletprovider.Renameitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters) Methode.

`Rename-ItemProperty` Sie können definieren, dass dynamische Parameter, die ausgelöst werden die `Path`, `Name`, und `NewName` Parameter von der `Rename-ItemProperty` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Idynamicpropertycmdletprovider.Renamepropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) Methode.

`Set-Content` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` Parameter der `Set-Content` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentwriterdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) Methode.

`Set-Item` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` und `Value` Parameter von der `Set-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Itemcmdletprovider.Setitemdynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) Methode.

`Set-ItemProperty` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` und `Value` Parameter von der `Set-Item` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Ipropertycmdletprovider.Setpropertydynamicparameters*](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters) Methode.

`Test-Path` Cmdlets können Sie dynamische Parameter, die ausgelöst werden definieren die `Path` Parameter der `Test-Path` Cmdlet, durch die Implementierung der [ System.Management.Automation.Provider.Itemcmdletprovider.Invokedefaultactiondynamicparameters*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) Methode.

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie ein Windows PowerShell-Anbieter](./writing-a-windows-powershell-provider.md)