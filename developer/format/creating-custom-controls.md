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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066684"
---
# <a name="creating-custom-controls"></a>Erstellen von benutzerdefinierten Steuerelementen

Benutzerdefinierte Steuerelemente sind der flexibelsten Komponenten eine Formatierungsdatei. Im Gegensatz zu der Tabelle, Liste und Breiten Ansichten, die definieren, eine formale Struktur der Daten, z. B. eine Tabelle mit Daten, können benutzerdefinierte Steuerelemente definieren, wie eine einzelne Dateneinheit angezeigt wird. Sie können definieren, einen gemeinsamen Satz von benutzerdefinierten Steuerelementen, die auf die Formatierungsdatei für alle Ansichten verfügbar sind, können Sie definieren, benutzerdefinierte Steuerelemente, die mit einer bestimmten Ansicht verfügbar sind oder Sie können definieren, einen Satz von Steuerelementen, die eine Gruppe von Objekten zur Verfügung stehen.

## <a name="custom-control-example"></a>Beispiel für ein benutzerdefiniertes Steuerelement

Das folgende Beispiel zeigt ein benutzerdefiniertes Steuerelement, das in der Datei Certificates.Format.ps1xml definiert ist. Dieses benutzerdefinierte Steuerelement dient zum Trennen der [System.Management.Automation.Signature](/dotnet/api/System.Management.Automation.Signature) Objekte, die in einer Tabellenansicht angezeigt.

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

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie eine Formatierungsdatei PowerShell](./writing-a-powershell-formatting-file.md)
