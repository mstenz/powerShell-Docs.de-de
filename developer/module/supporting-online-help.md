---
title: Unterstützung von Onlinehilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3204599c-7159-47aa-82ec-4a476f461027
caps.latest.revision: 7
ms.openlocfilehash: b76f45299d11dc10c8b16ed80f87c7f1fcc5ed65
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082140"
---
# <a name="supporting-online-help"></a>Unterstützung für Onlinehilfe

Ab Windows PowerShell 3.0 stehen zwei Methoden zur Unterstützung der `Get-Help` Online-Features für Windows PowerShell-Befehle. In diesem Thema wird erläutert, wie Sie dieses Feature für unterschiedliche Befehlstypen zu implementieren.

## <a name="about-online-help"></a>Informationen zu Online-Hilfe

Onlinehilfe war schon immer ein wesentlicher Bestandteil des Windows PowerShell. Obwohl die `Get-Help` Cmdlet zeigt die Hilfethemen an der Eingabeaufforderung an, die viele Benutzer bevorzugen die Erfahrung online zu lesen, einschließlich farbcodierung, links und Freigabe Ideen in Community-Inhalt und Wiki-basierten Dokumenten. Wichtiger ist, wird vor der Einführung der aktualisierbaren Hilfe, online-Hilfe die aktuelle Version der Hilfedateien bereitgestellt.

Mit dem Aufkommen der aktualisierbaren Hilfe in Windows PowerShell 3.0 spielt die Onlinehilfe weiterhin eine wichtige Rolle. Zusätzlich zu den flexibler Installationsoptionen enthält die Onlinehilfe zu Hilfe für Benutzer, die nicht oder können keine aktualisierbare Hilfe zum Herunterladen der Hilfethemen.

## <a name="how-get-help--online-works"></a>Wie Get-Help-Online funktioniert

Für Benutzer finden Sie die online-Hilfethemen für Befehle, die `Get-Help` Befehl verfügt über einen Parameter "Online", das die Onlineversion des Hilfethemas für einen Befehl im Standardinternetbrowser des Benutzers geöffnet wird.

Zum Beispiel der folgende Befehl für das Onlinehilfethema öffnet die `Invoke-Command` Cmdlet.

```powershell
Get-Help Invoke-Command -Online
```

Zum Implementieren `Get-Help` -Online, die `Get-Help` Cmdlet sucht für einen Uniform Resource Identifier (URI) für das Hilfethema für online-Version in den folgenden Speicherorten.

- Der erste Link im Abschnitt "Verwandte Links" des Hilfethemas für den Befehl. Das Hilfethema muss auf dem Computer des Benutzers installiert werden. Dieses Feature wurde in Windows PowerShell 2.0 eingeführt.

- Der "HelpUri"-Eigenschaft von einem der Befehle. Der "HelpUri"-Eigenschaft wird zugegriffen werden kann, selbst wenn das Hilfethema für den Befehl nicht auf dem Computer des Benutzers installiert ist. Dieses Feature wurde in Windows PowerShell 3.0 eingeführt.

  `Get-Help` Sucht für einen URI in den ersten Eintrag in "Verwandte Links" vor dem Abrufen des HelpUri-Eigenschaftswert. Wenn der Wert der Eigenschaft falsch ist oder geändert wurde, können Sie es überschreiben, indem Sie einen anderen Wert eingeben, in dem ersten dazugehörigen Link. Dem ersten dazugehörigen Link funktioniert jedoch nur, wenn die Hilfethemen auf dem Computer des Benutzers installiert sind.

## <a name="adding-a-uri-to-the-first-related-link-of-a-command-help-topic"></a>Einen URI hinzufügen, der dem ersten dazugehörigen Link eines Hilfethemas für den Befehl

Sie können die unterstützen `Get-Help` -Online für jeden Befehl, indem Sie einen gültigen URI an den ersten Eintrag im Abschnitt "Verwandte Links" des XML-basierte Hilfethemas für den Befehl hinzufügen. Diese Option ist nur in XML-basierte Hilfethemen und funktioniert nur, wenn das Hilfethema auf dem Computer des Benutzers installiert ist. Wenn das Hilfethema installiert ist, und der URI wird aufgefüllt, dieser Wert hat Vorrang vor den **HelpUri** Eigenschaft des Befehls. Weitere Informationen zu XML-Hilfethemen für Befehle, finden Sie unter [Writing XML-Based Hilfethemen zu Befehlen](../help/writing-xml-based-help-topics-for-commands.md).

Um dieses Feature zu unterstützen, muss der URI in angezeigt werden die `maml:uri` Element unterhalb der ersten `maml:relatedLinks/maml:navigationLink` Element in der `maml:relatedLinks` Element.

Das folgende XML zeigt die korrekte Platzierung des URI. Die "Online-Version:" Text in die `maml:linkText` Element ist eine bewährte Methode, aber es ist nicht erforderlich.

```xml

<maml:relatedLinks>
    <maml:navigationLink>
        <maml:linkText>Online version:</maml:linkText>
        <maml:uri>http://go.microsoft.com/fwlink/?LinkID=113279</maml:uri>
    </maml:navigationLink>
    <maml:navigationLink>
        <maml:linkText>about_History</maml:linkText>
        <maml:uri/>
    </maml:navigationLink>
</maml:relatedLinks>
```

## <a name="adding-the-helpuri-property-to-a-command"></a>Der "HelpUri"-Eigenschaft hinzufügen auf einen Befehl

In diesem Abschnitt wird gezeigt, wie Befehle mit unterschiedlichen Typen der "HelpUri"-Eigenschaft hinzugefügt.

### <a name="adding-a-helpuri-property-to-a-cmdlet"></a>Hinzufügen einer HelpUri-Eigenschaft zu einem Cmdlet

Für Cmdlets, die in geschriebenen C#, Hinzufügen einer **HelpUri** -Attribut auf die Cmdlet-Klasse. Der Wert des Attributs muss ein URI sein, die mit "http" oder "Https" beginnt.

Der folgende Code zeigt das HelpUri-Attribut des der `Get-History` Cmdlet-Klasse.

```
[Cmdlet(VerbsCommon.Get, "History", HelpUri = "http://go.microsoft.com/fwlink/?LinkID=001122")]
```

### <a name="adding-a-helpuri-property-to-an-advanced-function"></a>Hinzufügen einer HelpUri-Eigenschaft eine erweiterte Funktion

Für erweiterte Funktionen Hinzufügen einer **HelpUri** Eigenschaft, um die **CmdletBinding** Attribut. Der Wert der Eigenschaft muss ein URI sein, die mit "http" oder "Https" beginnt.

Der folgende Code zeigt das HelpUri-Attribut der New-Calendar-Funktion

```powershell

function New-Calendar {
    [CmdletBinding(SupportsShouldProcess=$true,
    HelpURI="http://go.microsoft.com/fwlink/?LinkID=01122")]
```

### <a name="adding-a-helpuri-attribute-to-a-cim-command"></a>Hinzufügen eines HelpUri-Attributs zu einem CIM-Befehl

CIM-Befehle, Hinzufügen einer **HelpUri** -Attribut auf die **CmdletMetadata** Element in der CDXML-Datei. Der Wert des Attributs muss ein URI sein, die mit "http" oder "Https" beginnt.

Der folgende Code zeigt das HelpUri-Attribut des Start-Debug-CIM-Befehls

```
<CmdletMetadata Verb="Debug" HelpUri="http://go.microsoft.com/fwlink/?LinkID=001122"/>
```

### <a name="adding-a-helpuri-attribute-to-a-workflow"></a>Hinzufügen eines HelpUri-Attributs zu einem Workflow

Für Workflows, die in der Windows PowerShell-Sprache geschrieben werden, Hinzufügen einer **. ExternalHelp** Comment-Anweisung an den Workflowcode. Der Wert der Richtlinie muss ein URI sein, die mit "http" oder "Https" beginnt.

> [!NOTE]
> Der "HelpUri"-Eigenschaft wird für XAML-basierten Workflows in Windows PowerShell nicht unterstützt.

Der folgende code zeigt die. ExternalHelp-Direktive in einer Workflowdatei.

```powershell
# .ExternalHelp "http://go.microsoft.com/fwlink/?LinkID=138338"
```