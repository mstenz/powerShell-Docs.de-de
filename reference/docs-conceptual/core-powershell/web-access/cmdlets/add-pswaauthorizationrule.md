---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "Hinzufügen von pswaauthorizationrule"
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 196797215a678e6f674592dc6b289816aced3c01
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="0aca1-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0aca1-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="0aca1-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="0aca1-104">SYNOPSIS</span></span>

<span data-ttu-id="0aca1-105">Fügt dem Windows PowerShell® Web Access-Autorisierungsregelsatz eine neue Autorisierungsregel hinzu.</span><span class="sxs-lookup"><span data-stu-id="0aca1-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="0aca1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0aca1-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="0aca1-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="0aca1-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="0aca1-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="0aca1-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="0aca1-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="0aca1-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="0aca1-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="0aca1-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="0aca1-111">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="0aca1-111">DESCRIPTION</span></span>

<span data-ttu-id="0aca1-112">Das Cmdlet **Add-PswaAuthorizationRule** fügt dem Windows PowerShell® Web Access-Autorisierungsregelsatz eine neue Autorisierungsregel hinzu.</span><span class="sxs-lookup"><span data-stu-id="0aca1-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="0aca1-113">Sie müssen die Benutzer, Computer und Windows PowerShell-Endpunkte für diese Regel angeben.</span><span class="sxs-lookup"><span data-stu-id="0aca1-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="0aca1-114">Sie können Benutzer und Computer entweder durch einzelne Benutzerkonten und Computernamen oder durch Gruppen angeben.</span><span class="sxs-lookup"><span data-stu-id="0aca1-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="0aca1-115">Bei einem Computer, der mit einer Active Directory-Domäne verknüpft ist, verwendet das Cmdlet die Sicherheits-ID (SID) des Computers, um die Regel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="0aca1-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="0aca1-116">Dadurch können Sie einen kurzen Namen, einen vollqualifizierten Domänennamen (FQDN) oder eine IP-Adresse für das Feld **Computername** auf der Anmeldeseite verwenden.</span><span class="sxs-lookup"><span data-stu-id="0aca1-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="0aca1-117">Bei einem Computer, der nicht mit einer Active Directory-Domäne verknüpft ist, erstellt das Cmdlet eine Regel, indem der vom Administrator bereitgestellte Computername verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="0aca1-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="0aca1-118">Der Endbenutzer muss den Computernamen exakt so angeben, wie er in der Regel angezeigt wird, um sich erfolgreich mit diesem Computer zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="0aca1-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="0aca1-119">Wenn es in einem Netzwerk mehrere Computer mit dem gleichen Namen gibt, kann ein kurzer Name sich auf mehr als einen Computer beziehen.</span><span class="sxs-lookup"><span data-stu-id="0aca1-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="0aca1-120">Dies kann beim Herstellen einer Verbindung zu Mehrdeutigkeit führen.</span><span class="sxs-lookup"><span data-stu-id="0aca1-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="0aca1-121">Wenn zum Beispiel eine Regel für den Arbeitsgruppencomputer „*Server1* besteht, und ein neuer Computer namens *server1.contoso.com* mit dem Netzwerk verknüpft wird, ist die Überprüfung mithilfe der Autorisierungsregeln erfolgreich. Windows PowerShell Web Access versucht dann, eine Verbindung zu dem Computer namens „*Server1*“ herzustellen.</span><span class="sxs-lookup"><span data-stu-id="0aca1-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="0aca1-122">Es kann nicht garantiert werden, dass die Verbindung mit dem angegebenen Arbeitsgruppencomputer hergestellt werden kann. Der Versuch kann entweder für die Arbeitsgruppe oder den Domänencomputer namens „*Server1*“ unternommen werden.</span><span class="sxs-lookup"><span data-stu-id="0aca1-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="0aca1-123">Es wird empfohlen, dass Sie, wann immer es möglich ist, beim Erstellen einer Autorisierungsregel den FQDN für den Zielcomputer verwenden, um die Mehrdeutigkeit zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="0aca1-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="0aca1-124">Die Autorisierungsregeln werten die primären Anmeldeinformationen des Windows PowerShell Web Access-Benutzers aus, nicht die alternativen Anmeldeinformationen (der zweite Satz von Anmeldeinformationen, der im Abschnitt **Optionale Verbindungseinstellungen** der Anmeldeseite gefunden werden kann).</span><span class="sxs-lookup"><span data-stu-id="0aca1-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="0aca1-125">Ein Beispiel hierfür finden Sie unter Beispiel 6.</span><span class="sxs-lookup"><span data-stu-id="0aca1-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="0aca1-126">Parameter</span><span class="sxs-lookup"><span data-stu-id="0aca1-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="0aca1-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0aca1-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="0aca1-128">Gibt den Namen einer Computergruppe in Active Directory Domain Services (AD DS) oder von lokalen Gruppen, denen diese Regel Zugriff gewährt, an.</span><span class="sxs-lookup"><span data-stu-id="0aca1-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="0aca1-129">Aliase</span><span class="sxs-lookup"><span data-stu-id="0aca1-129">Aliases</span></span>                              | <span data-ttu-id="0aca1-130">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-130">none</span></span>                                 |
| <span data-ttu-id="0aca1-131">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="0aca1-131">Required?</span></span>                            | <span data-ttu-id="0aca1-132">wahr</span><span class="sxs-lookup"><span data-stu-id="0aca1-132">true</span></span>                                 |
| <span data-ttu-id="0aca1-133">Position?</span><span class="sxs-lookup"><span data-stu-id="0aca1-133">Position?</span></span>                            | <span data-ttu-id="0aca1-134">benannt</span><span class="sxs-lookup"><span data-stu-id="0aca1-134">named</span></span>                                |
| <span data-ttu-id="0aca1-135">Standardwert</span><span class="sxs-lookup"><span data-stu-id="0aca1-135">Default Value</span></span>                        | <span data-ttu-id="0aca1-136">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-136">none</span></span>                                 |
| <span data-ttu-id="0aca1-137">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0aca1-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0aca1-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0aca1-139">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0aca1-140">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="0aca1-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0aca1-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="0aca1-142">Gibt den Namen des Computers an, dem diese Regel Zugriff gewährt.</span><span class="sxs-lookup"><span data-stu-id="0aca1-142">Specifies the computer name to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="0aca1-143">Aliase</span><span class="sxs-lookup"><span data-stu-id="0aca1-143">Aliases</span></span>                              | <span data-ttu-id="0aca1-144">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-144">none</span></span>                                 |
| <span data-ttu-id="0aca1-145">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="0aca1-145">Required?</span></span>                            | <span data-ttu-id="0aca1-146">wahr</span><span class="sxs-lookup"><span data-stu-id="0aca1-146">true</span></span>                                 |
| <span data-ttu-id="0aca1-147">Position?</span><span class="sxs-lookup"><span data-stu-id="0aca1-147">Position?</span></span>                            | <span data-ttu-id="0aca1-148">benannt</span><span class="sxs-lookup"><span data-stu-id="0aca1-148">named</span></span>                                |
| <span data-ttu-id="0aca1-149">Standardwert</span><span class="sxs-lookup"><span data-stu-id="0aca1-149">Default Value</span></span>                        | <span data-ttu-id="0aca1-150">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-150">none</span></span>                                 |
| <span data-ttu-id="0aca1-151">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0aca1-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0aca1-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0aca1-153">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0aca1-154">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="0aca1-155">-ConfigurationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0aca1-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="0aca1-156">Gibt den Namen einer Windows PowerShell-Sitzungskonfiguration (auch als Runspaces bezeichnet) an, der diese Regel Zugriff gewährt.</span><span class="sxs-lookup"><span data-stu-id="0aca1-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="0aca1-157">Aliase</span><span class="sxs-lookup"><span data-stu-id="0aca1-157">Aliases</span></span>                              | <span data-ttu-id="0aca1-158">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-158">none</span></span>                                 |
| <span data-ttu-id="0aca1-159">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="0aca1-159">Required?</span></span>                            | <span data-ttu-id="0aca1-160">wahr</span><span class="sxs-lookup"><span data-stu-id="0aca1-160">true</span></span>                                 |
| <span data-ttu-id="0aca1-161">Position?</span><span class="sxs-lookup"><span data-stu-id="0aca1-161">Position?</span></span>                            | <span data-ttu-id="0aca1-162">benannt</span><span class="sxs-lookup"><span data-stu-id="0aca1-162">named</span></span>                                |
| <span data-ttu-id="0aca1-163">Standardwert</span><span class="sxs-lookup"><span data-stu-id="0aca1-163">Default Value</span></span>                        | <span data-ttu-id="0aca1-164">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-164">none</span></span>                                 |
| <span data-ttu-id="0aca1-165">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0aca1-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0aca1-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0aca1-167">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0aca1-168">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="0aca1-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="0aca1-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="0aca1-170">Gibt ein **PSCredential**-Objekt für ein Benutzerkonto an, das Sie zum Ändern der Windows PowerShell Web Access-Autorisierungsregeln verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="0aca1-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="0aca1-171">Wenn Sie diesen Parameter nicht hinzufügen, verwendet das Cmdlet das aktuell angemeldete Benutzerkonto.</span><span class="sxs-lookup"><span data-stu-id="0aca1-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="0aca1-172">Führen Sie zum Abrufen eines **PSCredential**-Objekts, das zum Hinzufügen von Autorisierungsregeln im Remotemodus erforderlich ist, das Cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) aus.</span><span class="sxs-lookup"><span data-stu-id="0aca1-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="0aca1-173">Aliase</span><span class="sxs-lookup"><span data-stu-id="0aca1-173">Aliases</span></span>                              | <span data-ttu-id="0aca1-174">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-174">none</span></span>                                 |
| <span data-ttu-id="0aca1-175">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="0aca1-175">Required?</span></span>                            | <span data-ttu-id="0aca1-176">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-176">false</span></span>                                |
| <span data-ttu-id="0aca1-177">Position?</span><span class="sxs-lookup"><span data-stu-id="0aca1-177">Position?</span></span>                            | <span data-ttu-id="0aca1-178">benannt</span><span class="sxs-lookup"><span data-stu-id="0aca1-178">named</span></span>                                |
| <span data-ttu-id="0aca1-179">Standardwert</span><span class="sxs-lookup"><span data-stu-id="0aca1-179">Default Value</span></span>                        | <span data-ttu-id="0aca1-180">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-180">none</span></span>                                 |
| <span data-ttu-id="0aca1-181">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0aca1-182">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-182">false</span></span>                                |
| <span data-ttu-id="0aca1-183">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0aca1-184">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="0aca1-185">-Force</span><span class="sxs-lookup"><span data-stu-id="0aca1-185">-Force</span></span>

<span data-ttu-id="0aca1-186">Erzwingt die Ausführung des Befehls ohne Aufforderung zur Bestätigung durch den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="0aca1-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="0aca1-187">Zusätzlich werden Sie zu einer Bestätigung aufgefordert, wenn Sie einen einfachen oder kurzen Computernamen eingeben (z.B. ein Name, der kein Domänenname und nicht vollqualifiziert ist).</span><span class="sxs-lookup"><span data-stu-id="0aca1-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="0aca1-188">Die Bestätigung ist aus Sicherheitsgründen erforderlich. Dadurch können Sie einen einfachen Namen zum Hinzufügen eines Computers nur verwenden, wenn der Computer sich in einer Arbeitsgruppe befindet.</span><span class="sxs-lookup"><span data-stu-id="0aca1-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||  
|-|-|
| <span data-ttu-id="0aca1-189">Aliase</span><span class="sxs-lookup"><span data-stu-id="0aca1-189">Aliases</span></span>                              | <span data-ttu-id="0aca1-190">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-190">none</span></span>                                 |
| <span data-ttu-id="0aca1-191">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="0aca1-191">Required?</span></span>                            | <span data-ttu-id="0aca1-192">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-192">false</span></span>                                |
| <span data-ttu-id="0aca1-193">Position?</span><span class="sxs-lookup"><span data-stu-id="0aca1-193">Position?</span></span>                            | <span data-ttu-id="0aca1-194">benannt</span><span class="sxs-lookup"><span data-stu-id="0aca1-194">named</span></span>                                |
| <span data-ttu-id="0aca1-195">Standardwert</span><span class="sxs-lookup"><span data-stu-id="0aca1-195">Default Value</span></span>                        | <span data-ttu-id="0aca1-196">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-196">none</span></span>                                 |
| <span data-ttu-id="0aca1-197">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0aca1-198">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-198">false</span></span>                                |
| <span data-ttu-id="0aca1-199">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0aca1-200">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="0aca1-201">-RuleName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0aca1-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="0aca1-202">Gibt den Anzeigenamen für diese Regel an.</span><span class="sxs-lookup"><span data-stu-id="0aca1-202">Specifies the friendly name for this rule.</span></span>

|||  
|-|-|
| <span data-ttu-id="0aca1-203">Aliase</span><span class="sxs-lookup"><span data-stu-id="0aca1-203">Aliases</span></span>                              | <span data-ttu-id="0aca1-204">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-204">none</span></span>                                 |
| <span data-ttu-id="0aca1-205">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="0aca1-205">Required?</span></span>                            | <span data-ttu-id="0aca1-206">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-206">false</span></span>                                |
| <span data-ttu-id="0aca1-207">Position?</span><span class="sxs-lookup"><span data-stu-id="0aca1-207">Position?</span></span>                            | <span data-ttu-id="0aca1-208">benannt</span><span class="sxs-lookup"><span data-stu-id="0aca1-208">named</span></span>                                |
| <span data-ttu-id="0aca1-209">Standardwert</span><span class="sxs-lookup"><span data-stu-id="0aca1-209">Default Value</span></span>                        | <span data-ttu-id="0aca1-210">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-210">none</span></span>                                 |
| <span data-ttu-id="0aca1-211">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0aca1-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0aca1-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0aca1-213">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0aca1-214">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="0aca1-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="0aca1-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="0aca1-216">Gibt den Namen für eine oder mehrere Benutzergruppen in AD DS oder für lokale Gruppen, denen diese Regel Zugriff gewährt, an.</span><span class="sxs-lookup"><span data-stu-id="0aca1-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="0aca1-217">Aliase</span><span class="sxs-lookup"><span data-stu-id="0aca1-217">Aliases</span></span>                              | <span data-ttu-id="0aca1-218">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-218">none</span></span>                                 |
| <span data-ttu-id="0aca1-219">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="0aca1-219">Required?</span></span>                            | <span data-ttu-id="0aca1-220">wahr</span><span class="sxs-lookup"><span data-stu-id="0aca1-220">true</span></span>                                 |
| <span data-ttu-id="0aca1-221">Position?</span><span class="sxs-lookup"><span data-stu-id="0aca1-221">Position?</span></span>                            | <span data-ttu-id="0aca1-222">benannt</span><span class="sxs-lookup"><span data-stu-id="0aca1-222">named</span></span>                                |
| <span data-ttu-id="0aca1-223">Standardwert</span><span class="sxs-lookup"><span data-stu-id="0aca1-223">Default Value</span></span>                        | <span data-ttu-id="0aca1-224">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-224">none</span></span>                                 |
| <span data-ttu-id="0aca1-225">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0aca1-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0aca1-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0aca1-227">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0aca1-228">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="0aca1-229">-UserName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="0aca1-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="0aca1-230">Gibt den Namen von einem oder mehreren Benutzern an, denen diese Regel Zugriff gewährt.</span><span class="sxs-lookup"><span data-stu-id="0aca1-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="0aca1-231">Beim Benutzernamen kann es sich um ein lokales Benutzerkonto auf dem Gatewaycomputer oder um einen Benutzer in AD DS handeln.</span><span class="sxs-lookup"><span data-stu-id="0aca1-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="0aca1-232">Das Format ist `domain\user` oder `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="0aca1-232">The format is `domain\user` or `computer\user`.</span></span>

|||  
|-|-|
| <span data-ttu-id="0aca1-233">Aliase</span><span class="sxs-lookup"><span data-stu-id="0aca1-233">Aliases</span></span>                              | <span data-ttu-id="0aca1-234">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-234">none</span></span>                                 |
| <span data-ttu-id="0aca1-235">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="0aca1-235">Required?</span></span>                            | <span data-ttu-id="0aca1-236">wahr</span><span class="sxs-lookup"><span data-stu-id="0aca1-236">true</span></span>                                 |
| <span data-ttu-id="0aca1-237">Position?</span><span class="sxs-lookup"><span data-stu-id="0aca1-237">Position?</span></span>                            | <span data-ttu-id="0aca1-238">1</span><span class="sxs-lookup"><span data-stu-id="0aca1-238">1</span></span>                                    |
| <span data-ttu-id="0aca1-239">Standardwert</span><span class="sxs-lookup"><span data-stu-id="0aca1-239">Default Value</span></span>                        | <span data-ttu-id="0aca1-240">keine</span><span class="sxs-lookup"><span data-stu-id="0aca1-240">none</span></span>                                 |
| <span data-ttu-id="0aca1-241">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0aca1-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0aca1-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="0aca1-243">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="0aca1-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0aca1-244">falsch</span><span class="sxs-lookup"><span data-stu-id="0aca1-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="0aca1-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="0aca1-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="0aca1-246">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="0aca1-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="0aca1-247">Weitere Informationen finden Sie unter [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="0aca1-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="0aca1-248">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="0aca1-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="0aca1-249">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0aca1-249">String</span></span>

<span data-ttu-id="0aca1-250">Dieses Cmdlet akzeptiert eine Zeichenfolge oder ein Array von Zeichenfolgen als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="0aca1-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="0aca1-251">String\[\]</span><span class="sxs-lookup"><span data-stu-id="0aca1-251">String\[\]</span></span>

<span data-ttu-id="0aca1-252">Dieses Cmdlet akzeptiert eine Zeichenfolge oder ein Array von Zeichenfolgen als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="0aca1-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="0aca1-253">Ausgaben</span><span class="sxs-lookup"><span data-stu-id="0aca1-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="0aca1-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0aca1-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="0aca1-255">Dieses Cmdlet gibt ein Objekt der Autorisierungsregel zurück.</span><span class="sxs-lookup"><span data-stu-id="0aca1-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="0aca1-256">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="0aca1-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="0aca1-257">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="0aca1-257">EXAMPLE 1</span></span>

<span data-ttu-id="0aca1-258">In diesem Beispiel wird Zugriff auf die Sitzungskonfiguration *PSWAEndpoint*, bei der es sich um einen eingeschränkten Runspace auf *srv2* handelt, für Benutzer der Gruppe *SMAdmins* gewährt.</span><span class="sxs-lookup"><span data-stu-id="0aca1-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="0aca1-259">**Hinweis**: Der Computername muss ein voll qualifizierter Domänenname (FQDN) sein.</span><span class="sxs-lookup"><span data-stu-id="0aca1-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="0aca1-260">Administratoren definieren eine eingeschränkte Sitzungskonfiguration bzw. einen Runspace. Dabei handelt es sich um einen begrenzten Bereich von Cmdlets und Aufgaben, die die Endbenutzer ausführen können.</span><span class="sxs-lookup"><span data-stu-id="0aca1-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="0aca1-261">Das Definieren eines eingeschränkten Runspaces kann verhindern, dass Benutzer auf andere Computer zugreifen, die sich nicht im zugelassenen Windows PowerShell®-Runspace befinden. Dadurch wird eine sicherere Verbindung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="0aca1-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="0aca1-262">Weitere Informationen finden Sie unter [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) oder [Install and Use Windows PowerShell Web Access (Installieren und Verwenden von Windows PowerShell Web Access)](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="0aca1-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="0aca1-263">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="0aca1-263">EXAMPLE 2</span></span>

<span data-ttu-id="0aca1-264">In diesem Beispiel wird Zugriff auf die Windows PowerShell-Standardsitzungskonfiguration, `Microsoft.PowerShell`, auf *srv2* für Benutzer in contoso\\user1, contoso\\user2, und contoso\\user3 gewährt.</span><span class="sxs-lookup"><span data-stu-id="0aca1-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="0aca1-265">Dieses Cmdlet erstellt drei Regeln (eine pro Person).</span><span class="sxs-lookup"><span data-stu-id="0aca1-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="0aca1-266">BEISPIEL 3</span><span class="sxs-lookup"><span data-stu-id="0aca1-266">EXAMPLE 3</span></span>

<span data-ttu-id="0aca1-267">In diesem Beispiel wird veranschaulicht, wie Benutzernamenwerte über die Pipeline eingegeben werden.</span><span class="sxs-lookup"><span data-stu-id="0aca1-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="0aca1-268">BEISPIEL 4</span><span class="sxs-lookup"><span data-stu-id="0aca1-268">EXAMPLE 4</span></span>

<span data-ttu-id="0aca1-269">In diesem Beispiel wird veranschaulicht, wie alle Parameter Werte aus der Pipeline nach Eigenschaftsname annehmen.</span><span class="sxs-lookup"><span data-stu-id="0aca1-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject | 
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru | 
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru | 
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="0aca1-270">BEISPIEL 5</span><span class="sxs-lookup"><span data-stu-id="0aca1-270">EXAMPLE 5</span></span>

<span data-ttu-id="0aca1-271">In diesem Beispiel wird eine Regel hinzugefügt, um dem lokalen Benutzer namens *PswaServer\\ChrisLocal* Zugriff auf den Server namens *srv1.contoso.com* zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="0aca1-271">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="0aca1-272">Dieses Beispiel veranschaulicht ein Szenario, in dem das Gateway sich in einer Arbeitsgruppe und der Zielcomputer sich in einer Domäne befindet.</span><span class="sxs-lookup"><span data-stu-id="0aca1-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="0aca1-273">Die Autorisierungsregel gilt für die lokalen Benutzer auf dem Gateway.</span><span class="sxs-lookup"><span data-stu-id="0aca1-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="0aca1-274">Der Benutzer muss einen zweiten Satz von Anmeldeinformationen im Bereich **Optionale Verbindungseinstellungen** auf der Windows PowerShell Web Access-Anmeldeseite angeben, um sich erfolgreich zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="0aca1-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="0aca1-275">Der Gatewayserver verwendet den zusätzlichen Satz von Anmeldeinformationen, um den Benutzer auf dem Zielcomputer zu authentifizieren, einem Server namens *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="0aca1-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="0aca1-276">BEISPIEL 6</span><span class="sxs-lookup"><span data-stu-id="0aca1-276">EXAMPLE 6</span></span>

<span data-ttu-id="0aca1-277">In diesem Beispiel wird allen Endbenutzern Zugriff auf alle Endpunkte aller Computer gewährt.</span><span class="sxs-lookup"><span data-stu-id="0aca1-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="0aca1-278">Dadurch werden die Autorisierungsregeln praktisch deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="0aca1-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="0aca1-279">**Hinweis**: Das Verwenden des Platzhalterzeichens `*` wird für sicherheitsrelevante Bereitstellungen nicht empfohlen. Es sollte nur für Testumgebungen in Betracht gezogen oder für Bereitstellungen verwendet werden, bei denen die Sicherheit gelockert werden kann.</span><span class="sxs-lookup"><span data-stu-id="0aca1-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="0aca1-280">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="0aca1-280">See Also</span></span>

- <span data-ttu-id="0aca1-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0aca1-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>
- <span data-ttu-id="0aca1-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0aca1-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>
- <span data-ttu-id="0aca1-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0aca1-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>
- <span data-ttu-id="0aca1-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0aca1-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>
- [<span data-ttu-id="0aca1-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="0aca1-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [<span data-ttu-id="0aca1-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="0aca1-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [<span data-ttu-id="0aca1-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="0aca1-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)
