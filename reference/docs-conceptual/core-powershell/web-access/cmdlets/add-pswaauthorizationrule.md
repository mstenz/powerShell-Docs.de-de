---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "Hinzufügen von pswaauthorizationrule"
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 12f5cc30d4e3f9cfdd739cacbbab96134077e50a
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2017
---
#  <a name="add-pswaauthorizationrule"></a>Add-PswaAuthorizationRule

##  <a name="synopsis"></a>ZUSAMMENFASSUNG

Fügt dem Windows PowerShell® Web Access-Autorisierungsregelsatz eine neue Autorisierungsregel hinzu.

## <a name="syntax"></a>Syntax

###  <a name="usergroupnamecomputergroupname"></a>UserGroupNameComputerGroupName
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usergroupnamecomputername"></a>UserGroupNameComputerName
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputergroupname"></a>UserNameComputerGroupName
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputername"></a>UserNameComputerName
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a>BESCHREIBUNG

Das Cmdlet **Add-PswaAuthorizationRule** fügt dem Windows PowerShell® Web Access-Autorisierungsregelsatz eine neue Autorisierungsregel hinzu.

Sie müssen die Benutzer, Computer und Windows PowerShell-Endpunkte für diese Regel angeben. Sie können Benutzer und Computer entweder durch einzelne Benutzerkonten und Computernamen oder durch Gruppen angeben.

Bei einem Computer, der mit einer Active Directory-Domäne verknüpft ist, verwendet das Cmdlet die Sicherheits-ID (SID) des Computers, um die Regel zu erstellen.
Dadurch können Sie einen kurzen Namen, einen vollqualifizierten Domänennamen (FQDN) oder eine IP-Adresse für das Feld **Computername** auf der Anmeldeseite verwenden.

Bei einem Computer, der nicht mit einer Active Directory-Domäne verknüpft ist, erstellt das Cmdlet eine Regel, indem der vom Administrator bereitgestellte Computername verwendet wird. Der Endbenutzer muss den Computernamen exakt so angeben, wie er in der Regel angezeigt wird, um sich erfolgreich mit diesem Computer zu verbinden.

Wenn es in einem Netzwerk mehrere Computer mit dem gleichen Namen gibt, kann ein kurzer Name sich auf mehr als einen Computer beziehen. Dies kann beim Herstellen einer Verbindung zu Mehrdeutigkeit führen. Wenn zum Beispiel eine Regel für den Arbeitsgruppencomputer „*Server1* besteht, und ein neuer Computer namens *server1.contoso.com* mit dem Netzwerk verknüpft wird, ist die Überprüfung mithilfe der Autorisierungsregeln erfolgreich. Windows PowerShell Web Access versucht dann, eine Verbindung zu dem Computer namens „*Server1*“ herzustellen. Es kann nicht garantiert werden, dass die Verbindung mit dem angegebenen Arbeitsgruppencomputer hergestellt werden kann. Der Versuch kann entweder für die Arbeitsgruppe oder den Domänencomputer namens „*Server1*“ unternommen werden. Es wird empfohlen, dass Sie, wann immer es möglich ist, beim Erstellen einer Autorisierungsregel den FQDN für den Zielcomputer verwenden, um die Mehrdeutigkeit zu reduzieren.

Die Autorisierungsregeln werten die primären Anmeldeinformationen des Windows PowerShell Web Access-Benutzers aus, nicht die alternativen Anmeldeinformationen (der zweite Satz von Anmeldeinformationen, der im Abschnitt **Optionale Verbindungseinstellungen** der Anmeldeseite gefunden werden kann). Ein Beispiel hierfür finden Sie unter Beispiel 6.

## <a name="parameters"></a>Parameter

### <a name="-computergroupnameltstringgt"></a>-ComputerGroupName&lt;String&gt;

Gibt den Namen einer Computergruppe in Active Directory Domain Services (AD DS) oder von lokalen Gruppen, denen diese Regel Zugriff gewährt, an.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | wahr                                 |
| Position?                            | benannt                                |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | True (ByPropertyName)                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-computernameltstringgt"></a>-ComputerName&lt;String&gt;

Gibt den Namen des Computers an, dem diese Regel Zugriff gewährt.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | wahr                                 |
| Position?                            | benannt                                |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | True (ByPropertyName)                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-configurationnameltstringgt"></a>-ConfigurationName&lt;String&gt;

Gibt den Namen einer Windows PowerShell-Sitzungskonfiguration (auch als Runspaces bezeichnet) an, der diese Regel Zugriff gewährt.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | wahr                                 |
| Position?                            | benannt                                |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | True (ByPropertyName)                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-credentialltpscredentialgt"></a>-Credential&lt;PSCredential&gt;

Gibt ein **PSCredential**-Objekt für ein Benutzerkonto an, das Sie zum Ändern der Windows PowerShell Web Access-Autorisierungsregeln verwenden möchten. Wenn Sie diesen Parameter nicht hinzufügen, verwendet das Cmdlet das aktuell angemeldete Benutzerkonto. Führen Sie zum Abrufen eines **PSCredential**-Objekts, das zum Hinzufügen von Autorisierungsregeln im Remotemodus erforderlich ist, das Cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) aus.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | benannt                                |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-force"></a>-Force

Erzwingt die Ausführung des Befehls ohne Aufforderung zur Bestätigung durch den Benutzer.
Zusätzlich werden Sie zu einer Bestätigung aufgefordert, wenn Sie einen einfachen oder kurzen Computernamen eingeben (z.B. ein Name, der kein Domänenname und nicht vollqualifiziert ist). Die Bestätigung ist aus Sicherheitsgründen erforderlich. Dadurch können Sie einen einfachen Namen zum Hinzufügen eines Computers nur verwenden, wenn der Computer sich in einer Arbeitsgruppe befindet.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | benannt                                |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | falsch                                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-rulenameltstringgt"></a>-RuleName&lt;String&gt;

Gibt den Anzeigenamen für diese Regel an.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | falsch                                |
| Position?                            | benannt                                |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | True (ByPropertyName)                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-usergroupnameltstringgt"></a>-UserGroupName&lt;String\[\]&gt;

Gibt den Namen für eine oder mehrere Benutzergruppen in AD DS oder für lokale Gruppen, denen diese Regel Zugriff gewährt, an.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | wahr                                 |
| Position?                            | benannt                                |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | True (ByPropertyName)                |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="-usernameltstringgt"></a>-UserName&lt;String\[\]&gt;

Gibt den Namen von einem oder mehreren Benutzern an, denen diese Regel Zugriff gewährt. Beim Benutzernamen kann es sich um ein lokales Benutzerkonto auf dem Gatewaycomputer oder um einen Benutzer in AD DS handeln.
Das Format ist `domain\user` oder `computer\user`.

|||  
|-|-|
| Aliase                              | keine                                 |
| Erforderlich?                            | wahr                                 |
| Position?                            | 1                                    |
| Standardwert                        | keine                                 |
| Pipelineeingaben akzeptieren?               | True (ByValue, ByPropertyName)       |
| Platzhalterzeichen akzeptieren?          | falsch                                |

### <a name="ltcommonparametersgt"></a>&lt;CommonParameters&gt;

Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.
Weitere Informationen finden Sie unter [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).

## <a name="inputs"></a>EINGABEN

###  <a name="string"></a>Zeichenfolge

Dieses Cmdlet akzeptiert eine Zeichenfolge oder ein Array von Zeichenfolgen als Eingabe.

###  <a name="string"></a>String\[\]

Dieses Cmdlet akzeptiert eine Zeichenfolge oder ein Array von Zeichenfolgen als Eingabe.

##  <a name="outputs"></a>Ausgaben

###   <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a>Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule

Dieses Cmdlet gibt ein Objekt der Autorisierungsregel zurück.

## <a name="examples"></a>BEISPIELE

### <a name="example-1"></a>BEISPIEL 1

In diesem Beispiel wird Zugriff auf die Sitzungskonfiguration *PSWAEndpoint*, bei der es sich um einen eingeschränkten Runspace auf *srv2* handelt, für Benutzer der Gruppe *SMAdmins* gewährt.
**Hinweis**: Der Computername muss ein voll qualifizierter Domänenname (FQDN) sein. Administratoren definieren eine eingeschränkte Sitzungskonfiguration bzw. einen Runspace. Dabei handelt es sich um einen begrenzten Bereich von Cmdlets und Aufgaben, die die Endbenutzer ausführen können. Das Definieren eines eingeschränkten Runspaces kann verhindern, dass Benutzer auf andere Computer zugreifen, die sich nicht im zugelassenen Windows PowerShell®-Runspace befinden. Dadurch wird eine sicherere Verbindung ermöglicht. Weitere Informationen finden Sie unter [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) oder [Install and Use Windows PowerShell Web Access (Installieren und Verwenden von Windows PowerShell Web Access)](../install-and-use-windows-powershell-web-access.md).

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a>BEISPIEL 2

In diesem Beispiel wird Zugriff auf die Windows PowerShell-Standardsitzungskonfiguration, `Microsoft.PowerShell`, auf *srv2* für Benutzer in contoso\\user1, contoso\\user2, und contoso\\user3 gewährt. Dieses Cmdlet erstellt drei Regeln (eine pro Person).

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a>BEISPIEL 3

In diesem Beispiel wird veranschaulicht, wie Benutzernamenwerte über die Pipeline eingegeben werden.

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a>BEISPIEL 4

In diesem Beispiel wird veranschaulicht, wie alle Parameter Werte aus der Pipeline nach Eigenschaftsname annehmen.

\
###   <a name="section-subheading"></a>{#section .subHeading}

<div class="subSection">

<div id="code-snippet-5" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Kopieren](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f'); „In Zwischenablage kopieren.“)

</div>

</div>

<div id="CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o = New-Object -TypeName PSObject | Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

</div>

</div>

</div>

</div>

</div>

###   <a name="section-1-subheading"></a>{#section-1 .subHeading}

<div class="subSection">

<div id="code-snippet-6" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Kopieren](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb'); „In Zwischenablage kopieren.“)

</div>

</div>

<div id="CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> $o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

</div>

### <a name="example-5-example-5-subheading"></a>BEISPIEL 5 {#example-5 .subHeading}

<div class="subSection">

In diesem Beispiel wird eine Regel hinzugefügt, um dem lokalen Benutzer namens *PswaServer\\ChrisLocal* Zugriff auf den Server namens *srv1.contoso.com* zu gewähren.

Dieses Beispiel veranschaulicht ein Szenario, in dem das Gateway sich in einer Arbeitsgruppe und der Zielcomputer sich in einer Domäne befindet. Die Autorisierungsregel gilt für die lokalen Benutzer auf dem Gateway. Der Benutzer muss einen zweiten Satz von Anmeldeinformationen im Bereich **Optionale Verbindungseinstellungen** auf der Windows PowerShell Web Access-Anmeldeseite angeben, um sich erfolgreich zu authentifizieren. Der Gatewayserver verwendet den zusätzlichen Satz von Anmeldeinformationen, um den Benutzer auf dem Zielcomputer zu authentifizieren, einem Server namens *srv1.contoso.com*.

\
<div id="code-snippet-7" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Kopieren](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3'); „In Zwischenablage kopieren.“)

</div>

</div>

<div id="CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell

</div>

</div>

</div>

</div>

</div>

### <a name="example-6-example-6-subheading"></a>BEISPIEL 6 {#example-6 .subHeading}

<div class="subSection">

In diesem Beispiel wird allen Endbenutzern Zugriff auf alle Endpunkte aller Computer gewährt.
Dadurch werden die Autorisierungsregeln praktisch deaktiviert.
**Hinweis**: Das Verwenden des Platzhalterzeichens `*` wird für sicherheitsrelevante Bereitstellungen nicht empfohlen. Es sollte nur für Testumgebungen in Betracht gezogen oder für Bereitstellungen verwendet werden, bei denen die Sicherheit gelockert werden kann.

\
<div id="code-snippet-8" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[Windows PowerShell]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[Kopieren](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076'); „In Zwischenablage kopieren.“)

</div>

</div>

<div id="CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076"
class="codeSnippetContainerCode" dir="ltr">

<div style="color:Black;">

    PS C:\> Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *

</div>

</div>

</div>

</div>

</div>

</div>

<a name="related-topics"></a>Verwandte Themen 
--------------


[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)\
\
[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)\
\
[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)\
\
[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)\
\
[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)\
\
[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)\
\
[Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936)