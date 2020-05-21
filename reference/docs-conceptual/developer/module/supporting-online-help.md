---
title: Unterstützung der Online Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: de25b099e61f82891daff87c4c73bb8cad9111a4
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83559980"
---
# <a name="supporting-online-help"></a>Unterstützung einer Onlinehilfe

Ab Windows PowerShell 3,0 gibt es zwei Möglichkeiten, das `Get-Help` Online Feature für Windows PowerShell-Befehle zu unterstützen. In diesem Thema wird erläutert, wie diese Funktion für verschiedene Befehls Typen implementiert wird.

## <a name="about-online-help"></a>Informationen zur Online Hilfe

Die Online Hilfe war immer ein wesentlicher Bestandteil von Windows PowerShell. Obwohl das `Get-Help` Cmdlet an der Eingabeaufforderung Hilfe Themen anzeigt, bevorzugen viele Benutzer das Lesen der Online Dokumentation, einschließlich Farbcodierung, Hyperlinks und Freigabe von Ideen in Communityinhalten und Wiki-basierten Dokumenten. Vor der Einführung der aktualisierbaren Hilfe stellte die Online Hilfe die aktuelle Version der Hilfedateien bereit.

Mit der Einführung der aktualisierbaren Hilfe in Windows PowerShell 3,0 spielt die Online Hilfe immer noch eine wichtige Rolle. Zusätzlich zur flexiblen Benutzer Darstellung bietet die Online Hilfe Benutzern Hilfe, die keine aktualisierbare Hilfe zum Herunterladen von Hilfe Themen verwenden können.

## <a name="how-get-help--online-works"></a>Funktionsweise von "Get-Help-Online"

Um Benutzern die Suche nach den Online Hilfe Themen für Befehle zu erleichtern, `Get-Help` verfügt der Befehl über einen Online-Parameter, der die Online Version des Hilfe Themas für einen Befehl im Standard Internet Browser des Benutzers öffnet.

Mit dem folgenden Befehl wird beispielsweise das Online Hilfethema für das `Invoke-Command` Cmdlet geöffnet.

```powershell
Get-Help Invoke-Command -Online
```

Zum Implementieren von `Get-Help` -Online `Get-Help` sucht das Cmdlet nach einem Uniform Resource Identifier (URI) für das Hilfethema der Online Version an den folgenden Speicherorten.

- Der erste Link im Abschnitt "Verwandte Links" des Hilfe Themas für den Befehl. Das Hilfethema muss auf dem Computer des Benutzers installiert sein. Diese Funktion wurde in Windows PowerShell 2,0 eingeführt.

- Die HelpUri-Eigenschaft eines beliebigen Befehls. Der Zugriff auf die HelpUri-Eigenschaft ist auch dann möglich, wenn das Hilfethema für den Befehl nicht auf dem Computer des Benutzers installiert ist. Diese Funktion wurde in Windows PowerShell 3,0 eingeführt.

  `Get-Help`sucht im ersten Eintrag im Abschnitt "Verwandte Links" nach einem URI, bevor der Wert der HelpUri-Eigenschaft erhalten wird. Wenn der Eigenschafts Wert falsch ist oder geändert wurde, können Sie ihn überschreiben, indem Sie im ersten verknüpften Link einen anderen Wert eingeben. Der erste Verwandte Link funktioniert jedoch nur, wenn die Hilfe Themen auf dem Computer des Benutzers installiert sind.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Hinzufügen eines URIs zum ersten verknüpften Link eines Befehls Hilfe Themas

Sie können `Get-Help` -Online für jeden Befehl unterstützen, indem Sie dem ersten Eintrag im Abschnitt "Verwandte Links" des XML-basierten Hilfe Themas für den Befehl einen gültigen URI hinzufügen. Diese Option ist nur in XML-basierten Hilfe Themen gültig und funktioniert nur, wenn das Hilfethema auf dem Computer des Benutzers installiert ist. Wenn das Hilfethema installiert ist und der URI aufgefüllt wird, hat dieser Wert Vorrang vor der **HelpUri** -Eigenschaft des Befehls.

Um diese Funktion zu unterstützen, muss der URI im- `maml:uri` Element unter dem ersten `maml:relatedLinks/maml:navigationLink` Element im-Element enthalten sein `maml:relatedLinks` .

Der folgende XML-Code zeigt die korrekte Platzierung des URI. Der Text "Online Version:" im- `maml:linkText` Element ist eine bewährte Vorgehensweise, aber er ist nicht erforderlich.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>https://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Hinzufügen der HelpUri-Eigenschaft zu einem Befehl

In diesem Abschnitt wird gezeigt, wie die HelpUri-Eigenschaft Befehlen verschiedener Typen hinzugefügt wird.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Hinzufügen einer HelpUri-Eigenschaft zu einem Cmdlet

Fügen Sie für in c# geschriebene Cmdlets der Cmdlet-Klasse ein **HelpUri** -Attribut hinzu. Der Wert des-Attributs muss ein URI sein, der mit "http" oder "https" beginnt.

Der folgende Code zeigt das HelpUri-Attribut der `Get-History` Cmdlet-Klasse.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "https://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Hinzufügen einer HelpUri-Eigenschaft zu einer erweiterten Funktion

Fügen Sie für erweiterte Funktionen eine **HelpUri** -Eigenschaft zum **cmdletbinding** -Attribut hinzu. Der Wert der Eigenschaft muss ein URI sein, der mit "http" oder "https" beginnt.

Der folgende Code zeigt das HelpUri-Attribut der New-Calendar-Funktion.

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="https://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Hinzufügen eines HelpUri-Attributs zu einem CIM-Befehl

Fügen Sie für CIM-Befehle dem **cmdletmetadata** -Element in der cdxml-Datei ein **HelpUri** -Attribut hinzu. Der Wert des-Attributs muss ein URI sein, der mit "http" oder "https" beginnt.

Der folgende Code zeigt das HelpUri-Attribut des Befehls Start-Debug CIM.

```
<CmdletMetadata Verb="Debug" HelpUri="https://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Hinzufügen eines HelpUri-Attributs zu einem Workflow

Fügen Sie für Workflows, die in der Windows PowerShell-Sprache geschrieben sind, ein hinzu **. Externalhelp** -Kommentar Anweisung an den Workflow Code. Der Wert der Direktive muss ein URI sein, der mit "http" oder "https" beginnt.

> [!NOTE]
> Die HelpUri-Eigenschaft wird für XAML-basierte Workflows in Windows PowerShell nicht unterstützt.

Der folgende Code zeigt den. Externalhelp-Direktive in einer Workflow Datei.

```powershell
# .ExternalHelp "https://go.microsoft.com/fwlink/?LinkID=138338"
```
