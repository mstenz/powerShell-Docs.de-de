---
title: Erstellen von benutzerdefinierten Steuerelementen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3baa406-cd33-4420-be5a-07ef09d93480
caps.latest.revision: 8
ms.openlocfilehash: 3504ab1d974c55e9279172d0e851961474ccb926
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363379"
---
# <a name="creating-custom-controls"></a><span data-ttu-id="48427-102">Erstellen von benutzerdefinierten Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="48427-102">Creating Custom Controls</span></span>

<span data-ttu-id="48427-103">Benutzerdefinierte Steuerelemente sind die flexibelsten Komponenten einer Formatierungs Datei.</span><span class="sxs-lookup"><span data-stu-id="48427-103">Custom controls are the most flexible components of a formatting file.</span></span> <span data-ttu-id="48427-104">Im Gegensatz zu Tabellen-, Listen-und breiten Ansichten, die eine formale Struktur von Daten definieren, z. b. eine Tabelle mit Daten, können Sie mit benutzerdefinierten Steuerelementen definieren, wie ein einzelnes Datenelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="48427-104">Unlike table, list, and wide views that define a formal structure of data, such as a table of data, custom controls allow you to define how an individual piece of data is displayed.</span></span> <span data-ttu-id="48427-105">Sie können einen allgemeinen Satz benutzerdefinierter Steuerelemente definieren, die für alle Sichten der Formatierungs Datei verfügbar sind. Sie können benutzerdefinierte Steuerelemente definieren, die für eine bestimmte Ansicht verfügbar sind, oder Sie können einen Satz von Steuerelementen definieren, die für eine Gruppe von Objekten verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="48427-105">You can define a common set of custom controls that are available to all the views of the formatting file, you can define custom controls that are available to a specific view, or you can define a set of controls that are available to a group of objects.</span></span>

## <a name="custom-control-example"></a><span data-ttu-id="48427-106">Beispiel für einen benutzerdefinierten</span><span class="sxs-lookup"><span data-stu-id="48427-106">Custom Control Example</span></span>

<span data-ttu-id="48427-107">Das folgende Beispiel zeigt ein benutzerdefiniertes Steuerelement, das in der Datei "Zertifikats. Format. ps1xml" definiert ist.</span><span class="sxs-lookup"><span data-stu-id="48427-107">The following example shows a custom control that is defined in the Certificates.Format.ps1xml file.</span></span> <span data-ttu-id="48427-108">Dieses benutzerdefinierte Steuerelement wird zum Trennen der [System. Management. Automation. Signature](/dotnet/api/System.Management.Automation.Signature) -Objekte verwendet, die in einer Tabellenansicht angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="48427-108">This custom control is used to separate the [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) objects displayed in a table view.</span></span>

```xml
<Controls>
  <Control>
    <Name>SignatureTypes-GroupingFormat</Name>
    <CustomControl>
      <CustomEntries>
        <CustomEntry>
          <CustomItem>
            <Frame>
              <LeftIndent>4</LeftIndent>
              <CustomItem>
                <Text AssemblyName="System.Management.Automation" BaseName="FileSystemProviderStrings"
                  ResourceId="DirectoryDisplayGrouping"/>
                <ExpressionBinding>
                  <ScriptBlock>split-path $_.Path</ScriptBlock>
                </ExpressionBinding>
                <NewLine/>
              </CustomItem>
            </Frame>
          </CustomItem>
        </CustomEntry>
      </CustomEntries>
    </CustomControl>
  </Control>
</Controls>

```

## <a name="see-also"></a><span data-ttu-id="48427-109">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="48427-109">See Also</span></span>

[<span data-ttu-id="48427-110">Schreiben einer PowerShell-Formatierungs Datei</span><span class="sxs-lookup"><span data-stu-id="48427-110">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
