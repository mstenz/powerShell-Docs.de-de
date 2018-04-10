---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Abrufen von pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 74c044c329d8b6a305b86c9056a7041fb5fd046b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="get-pswaauthorizationrule"></a>Get-PswaAuthorizationRule

## <a name="synopsis"></a>ZUSAMMENFASSUNG

Gibt einen Satz von Windows PowerShell® Web Access-Autorisierungsregeln zurück.

## <a name="syntax"></a>Syntax

### <a name="id"></a>ID
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a>Name
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a>BESCHREIBUNG

Das Cmdlet **Get-PswaAuthorizationRule** gibt einen Satz von Windows PowerShell® Web Access-Autorisierungsregeln zurück.
Wenn weder der **Id**-Parameter noch der **RuleName**-Parameter angegeben ist, listet dieses Cmdlet alle Regeln auf. Der **Id**-Parameter kann zum Filtern der Ergebnisse verwendet werden.

## <a name="parameters"></a>PARAMETER

### <a name="-idltint32gt"></a>-Id&lt;Int32\[\]&gt;

Gibt die Bezeichner (IDs) der Regeln an, die dieses Cmdlet erhalten soll. Wenn keine IDs angegeben werden, gibt dieses Cmdlet alle Autorisierungsregeln zurück.

|||
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | 2                                    |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | True (ByValue, ByPropertyName)       |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String\[\]&gt;

Gibt die Namen der abzurufenden Autorisierungsregeln an. Dieser Parameter gibt alle Regeln zurück, die exakt mit den Regelnamen der Zeichenfolgen in diesem Array übereinstimmen.

|||
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | wahr                                 |
| Position?                            | 2                                    |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | True (ByValue, ByPropertyName)       |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.
Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>EINGABEN

### <a name="int"></a>int\[\]

Dieses Cmdlet akzeptiert ein Array von Ganzzahlen oder ein Array von Zeichenfolgenwerten als Eingabe.

### <a name="string"></a>String\[\]

Dieses Cmdlet akzeptiert ein Array von Ganzzahlen oder ein Array von Zeichenfolgenwerten als Eingabe.

## <a name="outputs"></a>AUSGABEN

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Dieses Cmdlet erstellt ein „PswaAuthorizationRule“ als Ausgabe.


## <a name="examples"></a>BEISPIELE

### <a name="example-1"></a>BEISPIEL 1

In diesem Beispiel werden alle Regeln abgerufen.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a>BEISPIEL 2

In diesem Beispiel wird eine Regel mit der ID *2* erstellt.

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a>BEISPIEL 3 {#example-3 .subHeading}

In diesem Beispiel wird veranschaulicht, wie das Cmdlet einen Wert aus der Pipeline akzeptiert.
In diesem Cmdlet werden eine Regel-ID und ein Regelname übergeben.

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a>Verwandte Themen

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)