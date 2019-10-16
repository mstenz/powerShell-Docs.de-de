---
title: Dynamische Parameter für Anbieter-Cmdlets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f1069f7-8fa8-4622-9e2c-af29b0b961c2
caps.latest.revision: 6
ms.openlocfilehash: a50de014988336c473c565b506a73de1c864d7e0
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359949"
---
# <a name="provider-cmdlet-dynamic-parameters"></a>Dynamische Anbieter-Cmdlet-Parameter

Anbieter können dynamische Parameter definieren, die einem Anbieter-Cmdlet hinzugefügt werden, wenn der Benutzer einen bestimmten Wert für einen der statischen Parameter des Cmdlets angibt. Ein Anbieter kann z. b. verschiedene dynamische Parameter basierend auf dem Pfad hinzufügen, den der Benutzer angibt, wenn er die Cmdlets "`Get-Item`" oder "`Set-Item`" aufruft.

## <a name="dynamic-parameter-methods"></a>Dynamische Parameter Methoden

Dynamische Parameter werden definiert, indem eine der dynamischen Parameter Methoden implementiert wird, wie z. b [. System. Management. Automation. Provider. itemcmdletprovider. getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) und [. System. Management. Automation. Provider. itemcmdletprovider. setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters)s-Methoden. Diese Methoden geben ein Objekt mit öffentlichen Eigenschaften zurück, die mit Attributen versehen sind, die denen von eigenständigen Cmdlets ähneln. Im folgenden finden Sie ein Beispiel für eine Implementierung der [System. Management. Automation. Provider. itemcmdletprovider. getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) -Methode, die vom Zertifikat Anbieter stammt:

```csharp
protected override object GetItemDynamicParameters(string path)
{
    return new CertificateProviderDynamicParameters();
}
```

Im Gegensatz zu den statischen Parametern von Provider-Cmdlets können Sie die Eigenschaften dieser Parameter auf die gleiche Weise angeben, wie Parameter in eigenständigen Cmdlets definiert werden. Im folgenden finden Sie ein Beispiel für eine dynamische Parameter Klasse, die vom Zertifikat Anbieter übernommen wird:

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

Im folgenden finden Sie eine Liste der statischen Parameter, die verwendet werden können, um dynamische Parameter hinzuzufügen.

`Clear-Content`-Cmdlet Sie können dynamische Parameter definieren, die durch den `Path`-Parameter des Cmdlets Clear-Clear ausgelöst werden, indem Sie die [System. Management. Automation. Provider. icontentcmdletprovider. clearcontentdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContentDynamicParameters) implementieren. anzuwenden.

`Clear-Item`-Cmdlet Sie können dynamische Parameter definieren, die durch den `Path`-Parameter des `Clear-Item`-Cmdlets ausgelöst werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. clearitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ClearItemDynamicParameters) -Methode implementieren.

`Clear-ItemProperty`-Cmdlet Sie können dynamische Parameter definieren, die durch den `Path`-Parameter des `Clear-ItemProperty`-Cmdlets ausgelöst werden, indem Sie die [System. Management. Automation. Provider. ipropertycmdletprovider. clearpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.ClearPropertyDynamicParameters) -Methode implementieren. .

`Copy-Item`-Cmdlet Sie können dynamische Parameter definieren, die durch die Parameter `Path`, `Destination` und `Recurse` des `Copy-Item`-Cmdlets ausgelöst werden, indem Sie das [Cmdlet System. Management. Automation. Provider. containercmdletprovider. copyitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItemDynamicParameters) -Methode.

Cmdlet "Get-ChildItems" Sie können dynamische Parameter definieren, die durch die Parameter "`Path`" und "`Recurse`" des `Get-ChildItem`-Cmdlets ausgelöst werden, indem Sie das [Cmdlet System. Management. Automation. Provider. containercmdletprovider. getchilditemsdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItemsDynamicParameters) und [System. Management. Automation. Provider. containercmdletprovider. getchildnamesdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNamesDynamicParameters) -Methoden.

`Get-Content`-Cmdlet Sie können dynamische Parameter definieren, die durch den `Path`-Parameter des Cmdlets "`Get-Content`" ausgelöst werden, indem Sie " [System. Management. Automation. Provider. icontentcmdletprovider. getcontentreaderdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReaderDynamicParameters) " implementieren. anzuwenden.

`Get-Item`-Cmdlet Sie können dynamische Parameter definieren, die durch den `Path`-Parameter des `Get-Item`-Cmdlets ausgelöst werden, indem Sie die [System. Management. Automation. Provider. itemcmdletprovider. getitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItemDynamicParameters) -Methode implementieren.

`Get-ItemProperty`-Cmdlet Sie können dynamische Parameter definieren, die durch die Parameter "`Path`" und "`Name`" des `Get-ItemProperty`-Cmdlets ausgelöst werden, indem Sie " [System. Management. Automation. Provider. ipropertycmdletprovider. getpropertydynamicparameters *" implementieren. ](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.GetPropertyDynamicParameters)-Methode.

`Invoke-Item`-Cmdlet Sie können dynamische Parameter definieren, die durch den `Path`-Parameter des `Invoke-Item`-Cmdlets ausgelöst werden, indem Sie [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) implementieren. anzuwenden.

`Move-Item`-Cmdlet Sie können dynamische Parameter definieren, die durch die Parameter "`Path`" und "`Destination`" des `Move-Item`-Cmdlets ausgelöst werden, indem Sie " [System. Management. Automation. Provider. navigationcmdletprovider. muveitemdynamicparameters *" implementieren. ](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItemDynamicParameters)-Methode.

`New-Item`-Cmdlet Sie können dynamische Parameter definieren, die durch die Parameter `Path`, `ItemType` und `Value` des `New-Item`-Cmdlets ausgelöst werden, indem Sie das [Cmdlet System. Management. Automation. Provider. containercmdletprovider. netwitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItemDynamicParameters) -Methode.

`New-ItemProperty`-Cmdlet Sie können dynamische Parameter definieren, die durch die Parameter "`Path`", "`Name`", "`PropertyType`" und "`Value`" des `New-ItemProperty`-Cmdlets ausgelöst werden. implementieren Sie hierzu das [ System. Management. Automation. Provider. idynamicpropertycmdletprovider. newpropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.NewPropertyDynamicParameters) -Methode.

`New-PSDrive`-Cmdlet Sie können dynamische Parameter definieren, die vom [System. Management. Automation. psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -Objekt ausgelöst werden, das vom `New-PSDrive`-Cmdlet zurückgegeben wird, indem die [ System. Management. Automation. Provider. drivecmdletprovider. newdrivedynamicparameters *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) -Methode.

`Remove-Item` Sie können dynamische Parameter definieren, die durch die Parameter "`Path`" und "`Recurse`" des `Remove-Item`-Cmdlets ausgelöst werden, indem Sie " [System. Management. Automation. Provider. containercmdletprovider. removeitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItemDynamicParameters) " implementieren. anzuwenden.

`Remove-ItemProperty` Sie können dynamische Parameter definieren, die durch die Parameter "`Path`" und "`Name`" des `Remove-ItemProperty`-Cmdlets ausgelöst werden, indem Sie das [Cmdlet System. Management. Automation. Provider. idynamicpropertycmdletprovider. removepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RemovePropertyDynamicParameters) -Methode.

`Rename-Item`-Cmdlet Sie können dynamische Parameter definieren, die durch die Parameter "`Path`" und "`NewName`" des `Rename-Item`-Cmdlets ausgelöst werden, indem Sie " [System. Management. Automation. Provider. containercmdletprovider. renameitemdynamicparameters *" implementieren. ](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RenameItemDynamicParameters)-Methode.

`Rename-ItemProperty` Sie können dynamische Parameter definieren, die durch die Parameter `Path`, `Name` und `NewName` des `Rename-ItemProperty`-Cmdlets ausgelöst werden, indem Sie das [Cmdlet System. Management. Automation. Provider. idynamicpropertycmdletprovider. renamepropertydynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IDynamicPropertyCmdletProvider.RenamePropertyDynamicParameters) -Methode.

`Set-Content`-Cmdlet Sie können dynamische Parameter definieren, die durch den `Path`-Parameter des Cmdlets "`Set-Content`" ausgelöst werden, indem Sie " [System. Management. Automation. Provider. icontentcmdletprovider. getcontentschreiterdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentWriterDynamicParameters) " implementieren. anzuwenden.

`Set-Item`-Cmdlet Sie können dynamische Parameter definieren, die durch die Parameter "`Path`" und "`Value`" des `Set-Item`-Cmdlets ausgelöst werden, indem Sie " [System. Management. Automation. Provider. itemcmdletprovider. setitemdynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItemDynamicParameters) " implementieren. anzuwenden.

`Set-ItemProperty`-Cmdlet Sie können dynamische Parameter definieren, die durch die Parameter "`Path`" und "`Value`" des `Set-Item`-Cmdlets ausgelöst werden, indem Sie " [System. Management. Automation. Provider. ipropertycmdletprovider. setpropertydynamicparameters *" implementieren. ](/dotnet/api/System.Management.Automation.Provider.IPropertyCmdletProvider.SetPropertyDynamicParameters)-Methode.

`Test-Path`-Cmdlet Sie können dynamische Parameter definieren, die durch den `Path`-Parameter des `Test-Path`-Cmdlets ausgelöst werden, indem Sie [System. Management. Automation. Provider. itemcmdletprovider. invokedefaultactiondynamicparameters *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.InvokeDefaultActionDynamicParameters) implementieren. anzuwenden.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Anbieters](./writing-a-windows-powershell-provider.md)