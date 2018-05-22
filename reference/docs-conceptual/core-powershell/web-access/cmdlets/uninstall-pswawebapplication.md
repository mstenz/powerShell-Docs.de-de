---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Uninstall-PswaWebApplication
ms.openlocfilehash: b2a3e4d584fd04ee49e1e6408dba39fd8bc555dc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="uninstall-pswawebapplication"></a>Uninstall-PswaWebApplication

## <a name="synopsis"></a>ZUSAMMENFASSUNG

Deinstalliert die Windows PowerShell®-Webanwendung.

## <a name="syntax"></a>SYNTAX

### <a name="default"></a>Standardwert
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>BESCHREIBUNG

Das Cmdlet **Uninstall-PswaWebApplication** deinstalliert die Windows PowerShell-Webanwendung und entfernt die Website aus IIS. Durch das Cmdlet werden IIS oder andere installierte Features nicht deinstalliert, da sie für das Ausführen von Windows PowerShell erforderlich sind.

## <a name="parameters"></a>PARAMETER

### <a name="-deletetestcertificate"></a>-DeleteTestCertificate

Gibt an, dass die Testzertifikate, die mit dem Cmdlet **Install\_PswaWebApplication** (mit dem Parameter **UseTestCertificate**) erstellt wurden, gelöscht wurden.
Nur das Testzertifikat, das den gleichen Namen wie das hat, das mit dem Cmdlet **Install-PswaWebApplication** erstellt wurde, wurde gelöscht.

|||
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | benannt                                |
| Standardwert                        | wahr                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-webapplicationname-ltstringgt"></a>-WebApplicationName &lt;String&gt;

Gibt den Namen der zu deinstallierenden Webanwendung an.

|||
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | 1                                    |
| Standardwert                        | pswa                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-websitename-ltstringgt"></a>-WebSiteName &lt;String&gt;

Gibt den Namen der Website an, auf der die Webanwendung installiert wurde.

|||
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | benannt                                |
| Standardwert                        | Standardwebsite                     |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-confirm"></a>-Confirm

Sie werden vor dem Ausführen des Cmdlets zur Bestätigung aufgefordert.

|||
|-|-|
| Erforderlich?                            | falsch                                |
| Position?                            | benannt                                |
| Standardwert                        | falsch                                |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-whatif"></a>-WhatIf

Zeigt, was geschieht, wenn das Cmdlet ausgeführt wird.
Das Cmdlet wird nicht ausgeführt.

|||
|-|-|
| Erforderlich?                            | falsch                                |
| Position?                            | benannt                                |
| Standardwert                        | falsch                                |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.
Weitere Informationen finden Sie unter [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).

## <a name="inputs"></a>EINGABEN

Dieses Cmdlet unterstützt keine Eingabe.

## <a name="outputs"></a>AUSGABEN

Dieses Cmdlet gibt keine Ausgabe zurück.

## <a name="examples"></a>BEISPIELE

### <a name="example-1"></a>BEISPIEL 1

Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung.
Sie können dieses Cmdlet verwenden, um die Windows PowerShell-Webanwendung zu deinstallieren, wenn Sie diese mit den Standardwerten installiert haben.

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a>BEISPIEL 2

Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung und löscht das der Anwendung zugeordnete Testzertifikat.
Sie können dieses Cmdlet verwenden, um die Windows PowerShell-Webanwendung zu deinstallieren, wenn Sie diese mit den Standardwerten installiert und ein Testzertifikat erstellt haben.

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a>BEISPIEL 3 {#example-3 .subHeading}

Dieser Befehl deinstalliert die Windows PowerShell-Webanwendung, wenn während der Installation eine benutzerdefinierte Website und Anwendung angegeben wurden.
Dieser Befehl entfernt die Website namens *MySite* und die Anwendung namens *TestApplication*. Außerdem gibt er an, dass die der Anwendung zugeordneten Testzertifikate ebenfalls gelöscht werden.

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

## <a name="related-topics"></a>Verwandte Themen

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Install-PswaWebApplication](install-pswawebapplication.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)