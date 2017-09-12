---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Installieren von pswawebapplication
ms.technology: powershell
ms.openlocfilehash: a608a6272d3eae56ccf808b9d94525ca39df50cb
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="install-pswawebapplication"></a>Install-PswaWebApplication

## <a name="synopsis"></a>ZUSAMMENFASSUNG

Konfiguriert die Windows PowerShell® Web Access-Anwendung in IIS.

## <a name="syntax"></a>SYNTAX

### <a name="default"></a>Standardwert
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>BESCHREIBUNG

Das Cmdlet **Install-PswaWebApplication** konfiguriert die Windows PowerShell Web Access-Webanwendung. Dieser Befehl installiert die Webanwendung, ordnet sie einer Website zu und erstellt optional ein SSL-Testzertifikat mithilfe des Parameters **useTestCertificate**. Aus Sicherheitsgründen sollten Webadministratoren kein Testzertifikat für Produktionsumgebungen verwenden.

## <a name="parameters"></a>PARAMETER

### <a name="-usetestcertificate"></a>-UseTestCertificate

Gibt an, dass ein Testzertifikat erstellt wird. Wenn dieser Parameter auf „true“ festgelegt ist, erstellt dieses Cmdlet ein Testzertifikat und konfiguriert die Windows PowerShell Web Access-Webanwendung, damit das Zertifikat für HTTPS-Anforderungen verwendet wird. Wenn dieser Parameter auf „false“ festgelegt ist, wird kein Zertifikat bzw. keine Bindung erstellt. Legen Sie diesen Wert auf „false“ fest, wenn ein anderes Zertifikat für Windows PowerShell Web Access verwendet wird.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | benannt                                |
| Standardwert                        | wahr                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-webapplicationnameltstringgt"></a>-WebApplicationName&lt;String&gt;

Gibt den Namen Ihrer Webanwendung an. Dieser wird als letzter Teil der Windows PowerShell Web Access-URL angezeigt.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | 1                                    |
| Standardwert                        | pswa                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-websitenameltstringgt"></a>-WebSiteName&lt;String&gt;

Gibt den Namen der Website des Webservers (IIS) an, auf dem die Windows PowerShell Web Access-Webanwendung installiert werden soll.

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

Dieses Cmdlet erzeugt keine Ausgabe.

## <a name="examples"></a>BEISPIELE

### <a name="example-1"></a>BEISPIEL 1

In diesem Beispiel wird die PSWA-Webanwendung mithilfe der Standardwerte für die Parameter **WebApplicationName** (*pswa*) und **WebSiteName** (*Default Web Site*) installiert.

```
Install-PswaWebApplication
```

### <a name="example-2"></a>BEISPIEL 2

In diesem Beispiel wird die PSWA-Webanwendung mit einem Testzertifikat und den Standardwerten für die Parameter **WebApplicationName** und **WebSiteName** installiert.

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a>Verwandte Themen

- [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
- [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
- [Remove-PswaAuthorizationRule](remove-pswaauthorizationrule.md)
- [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
