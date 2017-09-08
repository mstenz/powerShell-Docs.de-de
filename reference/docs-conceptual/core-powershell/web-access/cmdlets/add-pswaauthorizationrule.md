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
#  <a name="add-pswaauthorizationrule"></a><span data-ttu-id="2dbfa-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2dbfa-103">Add-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="2dbfa-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="2dbfa-104">SYNOPSIS</span></span>

<span data-ttu-id="2dbfa-105">Fügt dem Windows PowerShell® Web Access-Autorisierungsregelsatz eine neue Autorisierungsregel hinzu.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="2dbfa-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2dbfa-106">Syntax</span></span>

###  <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="2dbfa-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="2dbfa-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usergroupnamecomputername"></a><span data-ttu-id="2dbfa-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="2dbfa-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputergroupname"></a><span data-ttu-id="2dbfa-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="2dbfa-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

###  <a name="usernamecomputername"></a><span data-ttu-id="2dbfa-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="2dbfa-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="2dbfa-111">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="2dbfa-111">DESCRIPTION</span></span>

<span data-ttu-id="2dbfa-112">Das Cmdlet **Add-PswaAuthorizationRule** fügt dem Windows PowerShell® Web Access-Autorisierungsregelsatz eine neue Autorisierungsregel hinzu.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="2dbfa-113">Sie müssen die Benutzer, Computer und Windows PowerShell-Endpunkte für diese Regel angeben.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="2dbfa-114">Sie können Benutzer und Computer entweder durch einzelne Benutzerkonten und Computernamen oder durch Gruppen angeben.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="2dbfa-115">Bei einem Computer, der mit einer Active Directory-Domäne verknüpft ist, verwendet das Cmdlet die Sicherheits-ID (SID) des Computers, um die Regel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="2dbfa-116">Dadurch können Sie einen kurzen Namen, einen vollqualifizierten Domänennamen (FQDN) oder eine IP-Adresse für das Feld **Computername** auf der Anmeldeseite verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="2dbfa-117">Bei einem Computer, der nicht mit einer Active Directory-Domäne verknüpft ist, erstellt das Cmdlet eine Regel, indem der vom Administrator bereitgestellte Computername verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="2dbfa-118">Der Endbenutzer muss den Computernamen exakt so angeben, wie er in der Regel angezeigt wird, um sich erfolgreich mit diesem Computer zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="2dbfa-119">Wenn es in einem Netzwerk mehrere Computer mit dem gleichen Namen gibt, kann ein kurzer Name sich auf mehr als einen Computer beziehen.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="2dbfa-120">Dies kann beim Herstellen einer Verbindung zu Mehrdeutigkeit führen.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="2dbfa-121">Wenn zum Beispiel eine Regel für den Arbeitsgruppencomputer „*Server1* besteht, und ein neuer Computer namens *server1.contoso.com* mit dem Netzwerk verknüpft wird, ist die Überprüfung mithilfe der Autorisierungsregeln erfolgreich. Windows PowerShell Web Access versucht dann, eine Verbindung zu dem Computer namens „*Server1*“ herzustellen.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="2dbfa-122">Es kann nicht garantiert werden, dass die Verbindung mit dem angegebenen Arbeitsgruppencomputer hergestellt werden kann. Der Versuch kann entweder für die Arbeitsgruppe oder den Domänencomputer namens „*Server1*“ unternommen werden.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="2dbfa-123">Es wird empfohlen, dass Sie, wann immer es möglich ist, beim Erstellen einer Autorisierungsregel den FQDN für den Zielcomputer verwenden, um die Mehrdeutigkeit zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="2dbfa-124">Die Autorisierungsregeln werten die primären Anmeldeinformationen des Windows PowerShell Web Access-Benutzers aus, nicht die alternativen Anmeldeinformationen (der zweite Satz von Anmeldeinformationen, der im Abschnitt **Optionale Verbindungseinstellungen** der Anmeldeseite gefunden werden kann).</span><span class="sxs-lookup"><span data-stu-id="2dbfa-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="2dbfa-125">Ein Beispiel hierfür finden Sie unter Beispiel 6.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="2dbfa-126">Parameter</span><span class="sxs-lookup"><span data-stu-id="2dbfa-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="2dbfa-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="2dbfa-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="2dbfa-128">Gibt den Namen einer Computergruppe in Active Directory Domain Services (AD DS) oder von lokalen Gruppen, denen diese Regel Zugriff gewährt, an.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="2dbfa-129">Aliase</span><span class="sxs-lookup"><span data-stu-id="2dbfa-129">Aliases</span></span>                              | <span data-ttu-id="2dbfa-130">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-130">none</span></span>                                 |
| <span data-ttu-id="2dbfa-131">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-131">Required?</span></span>                            | <span data-ttu-id="2dbfa-132">wahr</span><span class="sxs-lookup"><span data-stu-id="2dbfa-132">true</span></span>                                 |
| <span data-ttu-id="2dbfa-133">Position?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-133">Position?</span></span>                            | <span data-ttu-id="2dbfa-134">benannt</span><span class="sxs-lookup"><span data-stu-id="2dbfa-134">named</span></span>                                |
| <span data-ttu-id="2dbfa-135">Standardwert</span><span class="sxs-lookup"><span data-stu-id="2dbfa-135">Default Value</span></span>                        | <span data-ttu-id="2dbfa-136">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-136">none</span></span>                                 |
| <span data-ttu-id="2dbfa-137">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2dbfa-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="2dbfa-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="2dbfa-139">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2dbfa-140">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="2dbfa-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="2dbfa-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="2dbfa-142">Gibt den Namen des Computers an, dem diese Regel Zugriff gewährt.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-142">Specifies the computer name to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="2dbfa-143">Aliase</span><span class="sxs-lookup"><span data-stu-id="2dbfa-143">Aliases</span></span>                              | <span data-ttu-id="2dbfa-144">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-144">none</span></span>                                 |
| <span data-ttu-id="2dbfa-145">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-145">Required?</span></span>                            | <span data-ttu-id="2dbfa-146">wahr</span><span class="sxs-lookup"><span data-stu-id="2dbfa-146">true</span></span>                                 |
| <span data-ttu-id="2dbfa-147">Position?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-147">Position?</span></span>                            | <span data-ttu-id="2dbfa-148">benannt</span><span class="sxs-lookup"><span data-stu-id="2dbfa-148">named</span></span>                                |
| <span data-ttu-id="2dbfa-149">Standardwert</span><span class="sxs-lookup"><span data-stu-id="2dbfa-149">Default Value</span></span>                        | <span data-ttu-id="2dbfa-150">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-150">none</span></span>                                 |
| <span data-ttu-id="2dbfa-151">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2dbfa-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="2dbfa-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="2dbfa-153">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2dbfa-154">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="2dbfa-155">-ConfigurationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="2dbfa-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="2dbfa-156">Gibt den Namen einer Windows PowerShell-Sitzungskonfiguration (auch als Runspaces bezeichnet) an, der diese Regel Zugriff gewährt.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="2dbfa-157">Aliase</span><span class="sxs-lookup"><span data-stu-id="2dbfa-157">Aliases</span></span>                              | <span data-ttu-id="2dbfa-158">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-158">none</span></span>                                 |
| <span data-ttu-id="2dbfa-159">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-159">Required?</span></span>                            | <span data-ttu-id="2dbfa-160">wahr</span><span class="sxs-lookup"><span data-stu-id="2dbfa-160">true</span></span>                                 |
| <span data-ttu-id="2dbfa-161">Position?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-161">Position?</span></span>                            | <span data-ttu-id="2dbfa-162">benannt</span><span class="sxs-lookup"><span data-stu-id="2dbfa-162">named</span></span>                                |
| <span data-ttu-id="2dbfa-163">Standardwert</span><span class="sxs-lookup"><span data-stu-id="2dbfa-163">Default Value</span></span>                        | <span data-ttu-id="2dbfa-164">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-164">none</span></span>                                 |
| <span data-ttu-id="2dbfa-165">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2dbfa-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="2dbfa-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="2dbfa-167">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2dbfa-168">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="2dbfa-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="2dbfa-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="2dbfa-170">Gibt ein **PSCredential**-Objekt für ein Benutzerkonto an, das Sie zum Ändern der Windows PowerShell Web Access-Autorisierungsregeln verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="2dbfa-171">Wenn Sie diesen Parameter nicht hinzufügen, verwendet das Cmdlet das aktuell angemeldete Benutzerkonto.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="2dbfa-172">Führen Sie zum Abrufen eines **PSCredential**-Objekts, das zum Hinzufügen von Autorisierungsregeln im Remotemodus erforderlich ist, das Cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) aus.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="2dbfa-173">Aliase</span><span class="sxs-lookup"><span data-stu-id="2dbfa-173">Aliases</span></span>                              | <span data-ttu-id="2dbfa-174">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-174">none</span></span>                                 |
| <span data-ttu-id="2dbfa-175">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-175">Required?</span></span>                            | <span data-ttu-id="2dbfa-176">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-176">false</span></span>                                |
| <span data-ttu-id="2dbfa-177">Position?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-177">Position?</span></span>                            | <span data-ttu-id="2dbfa-178">benannt</span><span class="sxs-lookup"><span data-stu-id="2dbfa-178">named</span></span>                                |
| <span data-ttu-id="2dbfa-179">Standardwert</span><span class="sxs-lookup"><span data-stu-id="2dbfa-179">Default Value</span></span>                        | <span data-ttu-id="2dbfa-180">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-180">none</span></span>                                 |
| <span data-ttu-id="2dbfa-181">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2dbfa-182">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-182">false</span></span>                                |
| <span data-ttu-id="2dbfa-183">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2dbfa-184">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="2dbfa-185">-Force</span><span class="sxs-lookup"><span data-stu-id="2dbfa-185">-Force</span></span>

<span data-ttu-id="2dbfa-186">Erzwingt die Ausführung des Befehls ohne Aufforderung zur Bestätigung durch den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="2dbfa-187">Zusätzlich werden Sie zu einer Bestätigung aufgefordert, wenn Sie einen einfachen oder kurzen Computernamen eingeben (z.B. ein Name, der kein Domänenname und nicht vollqualifiziert ist).</span><span class="sxs-lookup"><span data-stu-id="2dbfa-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="2dbfa-188">Die Bestätigung ist aus Sicherheitsgründen erforderlich. Dadurch können Sie einen einfachen Namen zum Hinzufügen eines Computers nur verwenden, wenn der Computer sich in einer Arbeitsgruppe befindet.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||  
|-|-|
| <span data-ttu-id="2dbfa-189">Aliase</span><span class="sxs-lookup"><span data-stu-id="2dbfa-189">Aliases</span></span>                              | <span data-ttu-id="2dbfa-190">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-190">none</span></span>                                 |
| <span data-ttu-id="2dbfa-191">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-191">Required?</span></span>                            | <span data-ttu-id="2dbfa-192">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-192">false</span></span>                                |
| <span data-ttu-id="2dbfa-193">Position?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-193">Position?</span></span>                            | <span data-ttu-id="2dbfa-194">benannt</span><span class="sxs-lookup"><span data-stu-id="2dbfa-194">named</span></span>                                |
| <span data-ttu-id="2dbfa-195">Standardwert</span><span class="sxs-lookup"><span data-stu-id="2dbfa-195">Default Value</span></span>                        | <span data-ttu-id="2dbfa-196">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-196">none</span></span>                                 |
| <span data-ttu-id="2dbfa-197">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2dbfa-198">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-198">false</span></span>                                |
| <span data-ttu-id="2dbfa-199">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2dbfa-200">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="2dbfa-201">-RuleName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="2dbfa-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="2dbfa-202">Gibt den Anzeigenamen für diese Regel an.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-202">Specifies the friendly name for this rule.</span></span>

|||  
|-|-|
| <span data-ttu-id="2dbfa-203">Aliase</span><span class="sxs-lookup"><span data-stu-id="2dbfa-203">Aliases</span></span>                              | <span data-ttu-id="2dbfa-204">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-204">none</span></span>                                 |
| <span data-ttu-id="2dbfa-205">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-205">Required?</span></span>                            | <span data-ttu-id="2dbfa-206">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-206">false</span></span>                                |
| <span data-ttu-id="2dbfa-207">Position?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-207">Position?</span></span>                            | <span data-ttu-id="2dbfa-208">benannt</span><span class="sxs-lookup"><span data-stu-id="2dbfa-208">named</span></span>                                |
| <span data-ttu-id="2dbfa-209">Standardwert</span><span class="sxs-lookup"><span data-stu-id="2dbfa-209">Default Value</span></span>                        | <span data-ttu-id="2dbfa-210">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-210">none</span></span>                                 |
| <span data-ttu-id="2dbfa-211">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2dbfa-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="2dbfa-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="2dbfa-213">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2dbfa-214">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="2dbfa-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="2dbfa-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="2dbfa-216">Gibt den Namen für eine oder mehrere Benutzergruppen in AD DS oder für lokale Gruppen, denen diese Regel Zugriff gewährt, an.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||  
|-|-|
| <span data-ttu-id="2dbfa-217">Aliase</span><span class="sxs-lookup"><span data-stu-id="2dbfa-217">Aliases</span></span>                              | <span data-ttu-id="2dbfa-218">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-218">none</span></span>                                 |
| <span data-ttu-id="2dbfa-219">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-219">Required?</span></span>                            | <span data-ttu-id="2dbfa-220">wahr</span><span class="sxs-lookup"><span data-stu-id="2dbfa-220">true</span></span>                                 |
| <span data-ttu-id="2dbfa-221">Position?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-221">Position?</span></span>                            | <span data-ttu-id="2dbfa-222">benannt</span><span class="sxs-lookup"><span data-stu-id="2dbfa-222">named</span></span>                                |
| <span data-ttu-id="2dbfa-223">Standardwert</span><span class="sxs-lookup"><span data-stu-id="2dbfa-223">Default Value</span></span>                        | <span data-ttu-id="2dbfa-224">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-224">none</span></span>                                 |
| <span data-ttu-id="2dbfa-225">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2dbfa-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="2dbfa-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="2dbfa-227">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2dbfa-228">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="2dbfa-229">-UserName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="2dbfa-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="2dbfa-230">Gibt den Namen von einem oder mehreren Benutzern an, denen diese Regel Zugriff gewährt.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="2dbfa-231">Beim Benutzernamen kann es sich um ein lokales Benutzerkonto auf dem Gatewaycomputer oder um einen Benutzer in AD DS handeln.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="2dbfa-232">Das Format ist `domain\user` oder `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-232">The format is `domain\user` or `computer\user`.</span></span>

|||  
|-|-|
| <span data-ttu-id="2dbfa-233">Aliase</span><span class="sxs-lookup"><span data-stu-id="2dbfa-233">Aliases</span></span>                              | <span data-ttu-id="2dbfa-234">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-234">none</span></span>                                 |
| <span data-ttu-id="2dbfa-235">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-235">Required?</span></span>                            | <span data-ttu-id="2dbfa-236">wahr</span><span class="sxs-lookup"><span data-stu-id="2dbfa-236">true</span></span>                                 |
| <span data-ttu-id="2dbfa-237">Position?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-237">Position?</span></span>                            | <span data-ttu-id="2dbfa-238">1</span><span class="sxs-lookup"><span data-stu-id="2dbfa-238">1</span></span>                                    |
| <span data-ttu-id="2dbfa-239">Standardwert</span><span class="sxs-lookup"><span data-stu-id="2dbfa-239">Default Value</span></span>                        | <span data-ttu-id="2dbfa-240">keine</span><span class="sxs-lookup"><span data-stu-id="2dbfa-240">none</span></span>                                 |
| <span data-ttu-id="2dbfa-241">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="2dbfa-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="2dbfa-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="2dbfa-243">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="2dbfa-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="2dbfa-244">falsch</span><span class="sxs-lookup"><span data-stu-id="2dbfa-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="2dbfa-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="2dbfa-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="2dbfa-246">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="2dbfa-247">Weitere Informationen finden Sie unter [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="2dbfa-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="2dbfa-248">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="2dbfa-248">INPUTS</span></span>

###  <a name="string"></a><span data-ttu-id="2dbfa-249">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="2dbfa-249">String</span></span>

<span data-ttu-id="2dbfa-250">Dieses Cmdlet akzeptiert eine Zeichenfolge oder ein Array von Zeichenfolgen als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-250">This cmdlet accepts a string or an array of strings as input.</span></span>

###  <a name="string"></a><span data-ttu-id="2dbfa-251">String\[\]</span><span class="sxs-lookup"><span data-stu-id="2dbfa-251">String\[\]</span></span>

<span data-ttu-id="2dbfa-252">Dieses Cmdlet akzeptiert eine Zeichenfolge oder ein Array von Zeichenfolgen als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-252">This cmdlet accepts a string or an array of strings as input.</span></span>

##  <a name="outputs"></a><span data-ttu-id="2dbfa-253">Ausgaben</span><span class="sxs-lookup"><span data-stu-id="2dbfa-253">Outputs</span></span>

###   <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="2dbfa-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="2dbfa-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="2dbfa-255">Dieses Cmdlet gibt ein Objekt der Autorisierungsregel zurück.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="2dbfa-256">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="2dbfa-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="2dbfa-257">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="2dbfa-257">EXAMPLE 1</span></span>

<span data-ttu-id="2dbfa-258">In diesem Beispiel wird Zugriff auf die Sitzungskonfiguration *PSWAEndpoint*, bei der es sich um einen eingeschränkten Runspace auf *srv2* handelt, für Benutzer der Gruppe *SMAdmins* gewährt.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="2dbfa-259">**Hinweis**: Der Computername muss ein voll qualifizierter Domänenname (FQDN) sein.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="2dbfa-260">Administratoren definieren eine eingeschränkte Sitzungskonfiguration bzw. einen Runspace. Dabei handelt es sich um einen begrenzten Bereich von Cmdlets und Aufgaben, die die Endbenutzer ausführen können.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="2dbfa-261">Das Definieren eines eingeschränkten Runspaces kann verhindern, dass Benutzer auf andere Computer zugreifen, die sich nicht im zugelassenen Windows PowerShell®-Runspace befinden. Dadurch wird eine sicherere Verbindung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="2dbfa-262">Weitere Informationen finden Sie unter [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) oder [Install and Use Windows PowerShell Web Access (Installieren und Verwenden von Windows PowerShell Web Access)](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="2dbfa-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="2dbfa-263">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="2dbfa-263">EXAMPLE 2</span></span>

<span data-ttu-id="2dbfa-264">In diesem Beispiel wird Zugriff auf die Windows PowerShell-Standardsitzungskonfiguration, `Microsoft.PowerShell`, auf *srv2* für Benutzer in contoso\\user1, contoso\\user2, und contoso\\user3 gewährt.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="2dbfa-265">Dieses Cmdlet erstellt drei Regeln (eine pro Person).</span><span class="sxs-lookup"><span data-stu-id="2dbfa-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="2dbfa-266">BEISPIEL 3</span><span class="sxs-lookup"><span data-stu-id="2dbfa-266">EXAMPLE 3</span></span>

<span data-ttu-id="2dbfa-267">In diesem Beispiel wird veranschaulicht, wie Benutzernamenwerte über die Pipeline eingegeben werden.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="2dbfa-268">BEISPIEL 4</span><span class="sxs-lookup"><span data-stu-id="2dbfa-268">EXAMPLE 4</span></span>

<span data-ttu-id="2dbfa-269">In diesem Beispiel wird veranschaulicht, wie alle Parameter Werte aus der Pipeline nach Eigenschaftsname annehmen.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

\
###   <a name="section-subheading"></a><span data-ttu-id="2dbfa-270">{#section .subHeading}</span><span class="sxs-lookup"><span data-stu-id="2dbfa-270">{#section .subHeading}</span></span>

<div class="subSection">

<div id="code-snippet-5" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="2dbfa-271">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2dbfa-271">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="2dbfa-272">Kopieren</span><span class="sxs-lookup"><span data-stu-id="2dbfa-272">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_b61200ba-32cd-4df3-80be-7d5cf0ff709f'); „In Zwischenablage kopieren.“)

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

###   <a name="section-1-subheading"></a><span data-ttu-id="2dbfa-273">{#section-1 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="2dbfa-273">{#section-1 .subHeading}</span></span>

<div class="subSection">

<div id="code-snippet-6" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="2dbfa-274">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2dbfa-274">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="2dbfa-275">Kopieren</span><span class="sxs-lookup"><span data-stu-id="2dbfa-275">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c76e1b6c-cb67-4223-a7d0-54ec6b63bbcb'); „In Zwischenablage kopieren.“)

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

### <a name="example-5-example-5-subheading"></a><span data-ttu-id="2dbfa-276">BEISPIEL 5 {#example-5 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="2dbfa-276">EXAMPLE 5 {#example-5 .subHeading}</span></span>

<div class="subSection">

<span data-ttu-id="2dbfa-277">In diesem Beispiel wird eine Regel hinzugefügt, um dem lokalen Benutzer namens *PswaServer\\ChrisLocal* Zugriff auf den Server namens *srv1.contoso.com* zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-277">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="2dbfa-278">Dieses Beispiel veranschaulicht ein Szenario, in dem das Gateway sich in einer Arbeitsgruppe und der Zielcomputer sich in einer Domäne befindet.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-278">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="2dbfa-279">Die Autorisierungsregel gilt für die lokalen Benutzer auf dem Gateway.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-279">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="2dbfa-280">Der Benutzer muss einen zweiten Satz von Anmeldeinformationen im Bereich **Optionale Verbindungseinstellungen** auf der Windows PowerShell Web Access-Anmeldeseite angeben, um sich erfolgreich zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-280">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="2dbfa-281">Der Gatewayserver verwendet den zusätzlichen Satz von Anmeldeinformationen, um den Benutzer auf dem Zielcomputer zu authentifizieren, einem Server namens *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-281">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

\
<div id="code-snippet-7" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="2dbfa-282">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2dbfa-282">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="2dbfa-283">Kopieren</span><span class="sxs-lookup"><span data-stu-id="2dbfa-283">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7572cdeb-8835-49ed-9d8e-d3318eb639d3'); „In Zwischenablage kopieren.“)

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

### <a name="example-6-example-6-subheading"></a><span data-ttu-id="2dbfa-284">BEISPIEL 6 {#example-6 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="2dbfa-284">EXAMPLE 6 {#example-6 .subHeading}</span></span>

<div class="subSection">

<span data-ttu-id="2dbfa-285">In diesem Beispiel wird allen Endbenutzern Zugriff auf alle Endpunkte aller Computer gewährt.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-285">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="2dbfa-286">Dadurch werden die Autorisierungsregeln praktisch deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-286">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="2dbfa-287">**Hinweis**: Das Verwenden des Platzhalterzeichens `*` wird für sicherheitsrelevante Bereitstellungen nicht empfohlen. Es sollte nur für Testumgebungen in Betracht gezogen oder für Bereitstellungen verwendet werden, bei denen die Sicherheit gelockert werden kann.</span><span class="sxs-lookup"><span data-stu-id="2dbfa-287">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

\
<div id="code-snippet-8" class="codeSnippetContainer" xmlns="">

<div class="codeSnippetContainerTabs">

<div class="codeSnippetContainerTabSingle" dir="ltr">

[<span data-ttu-id="2dbfa-288">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2dbfa-288">Windows PowerShell</span></span>]()

</div>

</div>

<div class="codeSnippetContainerCodeContainer">

<div class="codeSnippetToolBar">

<div class="codeSnippetToolBarText">

[<span data-ttu-id="2dbfa-289">Kopieren</span><span class="sxs-lookup"><span data-stu-id="2dbfa-289">Copy</span></span>](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_9fb751ca-1e50-4411-a9a9-3343fe888076'); „In Zwischenablage kopieren.“)

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

<a name="related-topics"></a><span data-ttu-id="2dbfa-290">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="2dbfa-290">Related topics</span></span> 
--------------


<span data-ttu-id="2dbfa-291">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="2dbfa-291">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="2dbfa-292">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="2dbfa-292">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="2dbfa-293">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="2dbfa-293">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="2dbfa-294">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)\\</span><span class="sxs-lookup"><span data-stu-id="2dbfa-294">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)\\</span></span>
\
<span data-ttu-id="2dbfa-295">[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)\\</span><span class="sxs-lookup"><span data-stu-id="2dbfa-295">[Add-Member](http://go.microsoft.com/fwlink/p/?LinkId=113280)\\</span></span>
\
<span data-ttu-id="2dbfa-296">[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)\\</span><span class="sxs-lookup"><span data-stu-id="2dbfa-296">[New-Object](http://go.microsoft.com/fwlink/p/?LinkId=113355)\\</span></span>
\
[<span data-ttu-id="2dbfa-297">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="2dbfa-297">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)