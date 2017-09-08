---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Entfernen von pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: d316cb98efc730ed3e99f6a5dac2b969e3437129
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2017
---
#  <a name="remove-pswaauthorizationrule"></a>Remove-PswaAuthorizationRule

##  <a name="synopsis"></a>ZUSAMMENFASSUNG

Entfernt eine angegebene Autorisierungsregel aus Windows PowerShell® Web Access.

## <a name="syntax"></a>SYNTAX

###  <a name="id"></a>Id
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a>Regel
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a>BESCHREIBUNG

Entfernt eine angegebene Autorisierungsregel aus Windows PowerShell Web Access.

## <a name="parameters"></a>PARAMETER

### <a name="-force"></a>-Force

Führt das Cmdlet aus, ohne zur Bestätigung aufzufordern. Das Cmdlet fordert standardmäßig eine Bestätigung, bevor Sie fortfahren.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | benannt                                |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-id-ltint32gt"></a>-Id &lt;Int32\[\]&gt;

Gibt den Bezeichner (ID) von einer oder mehrerer Regeln an, die entfernt werden sollen.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | wahr                                 |
| Position?                            | 2                                    |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | True (ByValue, ByPropertyName)       |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a>-Rule &lt;PswaAuthorizationRule\[\]&gt;

Gibt die zu entfernenden Regeln an.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | wahr                                 |
| Position?                            | 2                                    |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | True (ByValue)                       |
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

Zeigt, was geschieht, wenn das Cmdlet ausgeführt wird. Das Cmdlet wird nicht ausgeführt.

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

###  <a name="int"></a>int\[\]

Dieses Cmdlet akzeptiert ein Array aus Ganzzahlen oder ein Array aus „PswaAuthorizationRule“-Objekten.

###  <a name="pswaauthorizationrule"></a>PswaAuthorizationRule\[\]

Dieses Cmdlet akzeptiert ein Array aus Ganzzahlen oder ein Array aus „PswaAuthorizationRule“-Objekten.

##  <a name="outputs"></a>AUSGABEN

Dieses Cmdlet erzeugt keine Ausgabe.

## <a name="examples"></a>BEISPIELE

### <a name="example-1"></a>BEISPIEL 1

In diesem Beispiel wird die Autorisierungsregel mit der ID *2* entfernt.

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a>BEISPIEL 2 {#example-2 .subHeading}

In diesem Beispiel werden alle Autorisierungsregel entfernt, außerdem ist die Bestätigung durch den Benutzer erforderlich.

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

##  <a name="related-topics"></a>Verwandte Themen

-  [Add-PswaAuthorizationRule](add-pswaauthorizationrule.md)
-  [Get-PswaAuthorizationRule](get-pswaauthorizationrule.md)
-  [Install-PswaWebApplication](install-pswawebapplication.md)
-  [Test-PswaAuthorizationRule](test-pswaauthorizationrule.md)
