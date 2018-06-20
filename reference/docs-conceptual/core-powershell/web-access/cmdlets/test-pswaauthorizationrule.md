---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Test-PswaAuthorizationRule
ms.openlocfilehash: 08248e65be229f9d0f4d606d6c0d039d86ced054
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190144"
---
# <a name="test-pswaauthorizationrule"></a>Test-PswaAuthorizationRule

## <a name="synopsis"></a>ZUSAMMENFASSUNG

Überprüft, ob eine Regel für einen angegebenen Benutzer, Computer oder Endpunkt vorhanden ist.

## <a name="syntax"></a>SYNTAX

### <a name="computername"></a>ComputerName
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a>ConnectionUri
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a>BESCHREIBUNG

Das Cmdlet **Test-PswaAuthorizationRule** überprüft, ob eine Regel für einen bestimmten Benutzer, Computer oder Endpunkt vorhanden ist.
Dieses Cmdlet kann auch zum Testen von Autorisierungsregeln verwendet werden, um zu überprüfen, ob die Zugriffsanforderung eines bestimmten Benutzers, Computers oder Endpunkts autorisiert ist.
Dieses Cmdlet wertet standardmäßig alle Regeln in der Autorisierungsdatei aus.
Sie können jedoch eine Teilmenge von zu testenden Regeln angeben.

Sie können dieses Cmdlet für die Problembehandlung von Authentifizierungsfehlern verwenden.

Die Parameter dieses Cmdlets entsprechen den Feldern auf der Windows PowerShell® Web Access-Anmeldeseite.

## <a name="parameters"></a>PARAMETER

### <a name="-computername-ltstringgt"></a>-ComputerName &lt;String&gt;

Gibt den Namen des zu testenden Computers an.

|||
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | wahr                                 |
| Position?                            | 2                                    |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-configurationname-ltstringgt"></a>-ConfigurationName &lt;String&gt;

Gibt den Namen einer zu testenden Windows PowerShell-Sitzungskonfiguration (auch als Endpunkt oder Runspaces bezeichnet) an.

|||
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | 3                                    |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-connectionuri-lturigt"></a>-ConnectionUri &lt;Uri&gt;

Gibt die zu testende Verbindungs-URI an.

|||
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | wahr                                 |
| Position?                            | 2                                    |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-credential-ltpscredentialgt"></a>-Credential &lt;PSCredential&gt;

Gibt ein **PSCredential**-Objekt für ein Benutzerkonto an, das Sie zum Testen der Windows PowerShell Web Access-Autorisierungsregeln verwenden möchten. Wenn Sie diesen Parameter nicht hinzufügen, verwendet das Cmdlet das aktuell angemeldete Benutzerkonto. Führen Sie zum Abrufen eines **PSCredential**-Objekts, das zum Testen von Autorisierungsregeln im Remotemodus erforderlich ist, das Cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) aus.

|||
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | benannt                                |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

Gibt eine Teilmenge der zu testenden Regeln an. Wenn dieser Parameter nicht angegeben ist, testet dieses Cmdlet alle Autorisierungsregeln.

|||
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | benannt                                |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | True (ByValue)                       |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-username-ltstringgt"></a>-UserName &lt;String&gt;

Gibt den Namen des zu testenden Benutzers an.

|||
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | wahr                                 |
| Position?                            | 1                                    |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.
Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>EINGABEN

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Dieses Cmdlet akzeptiert ein Array von „PswaAuthorizationRule“-Objekten als Eingabe.

## <a name="outputs"></a>AUSGABEN

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]

Dieses Cmdlet stellt ein Array von „PswaAuthorizationRule“-Objekten als Ausgabe.

## <a name="examples"></a>BEISPIELE

### <a name="example-1"></a>BEISPIEL 1

In diesem Beispiel werden alle Autorisierungsregeln getestet, um alle Regeln anzuzeigen, die es dem Benutzer *contoso\\mhanson* ermöglichen, sich mit dem Computer *srv2* zu verbinden und eine Windows PowerShell-Sitzungskonfiguration namens *Test* zu verwenden.

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a>BEISPIEL 2

In diesem Beispiel werden alle Autorisierungsregeln getestet, um zu überprüfen, welche davon für den Benutzer *contoso\\mhanson* gelten.

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a>Verwandte Themen

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)