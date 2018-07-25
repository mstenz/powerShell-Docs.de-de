---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Add-PswaAuthorizationRule
schema: 2.0.0
ms.openlocfilehash: a8904ac36f7fd9fe3c649ad4ca709a98c31b63c3
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39094227"
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="5f803-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="5f803-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="5f803-104">ZUSAMMENFASSUNG</span><span class="sxs-lookup"><span data-stu-id="5f803-104">SYNOPSIS</span></span>

<span data-ttu-id="5f803-105">Fügt dem Windows PowerShell® Web Access-Autorisierungsregelsatz eine neue Autorisierungsregel hinzu.</span><span class="sxs-lookup"><span data-stu-id="5f803-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="5f803-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5f803-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="5f803-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="5f803-107">UserGroupNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="5f803-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="5f803-108">UserGroupNameComputerName</span></span>

```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="5f803-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="5f803-109">UserNameComputerGroupName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="5f803-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="5f803-110">UserNameComputerName</span></span>

```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="5f803-111">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="5f803-111">DESCRIPTION</span></span>

<span data-ttu-id="5f803-112">Das Cmdlet **Add-PswaAuthorizationRule** fügt dem Windows PowerShell® Web Access-Autorisierungsregelsatz eine neue Autorisierungsregel hinzu.</span><span class="sxs-lookup"><span data-stu-id="5f803-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="5f803-113">Sie müssen die Benutzer, Computer und Windows PowerShell-Endpunkte für diese Regel angeben.</span><span class="sxs-lookup"><span data-stu-id="5f803-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="5f803-114">Sie können Benutzer und Computer entweder durch einzelne Benutzerkonten und Computernamen oder durch Gruppen angeben.</span><span class="sxs-lookup"><span data-stu-id="5f803-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="5f803-115">Bei einem Computer, der mit einer Active Directory-Domäne verknüpft ist, verwendet das Cmdlet die Sicherheits-ID (SID) des Computers, um die Regel zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="5f803-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="5f803-116">Dadurch können Sie einen kurzen Namen, einen vollqualifizierten Domänennamen (FQDN) oder eine IP-Adresse für das Feld **Computername** auf der Anmeldeseite verwenden.</span><span class="sxs-lookup"><span data-stu-id="5f803-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="5f803-117">Bei einem Computer, der nicht mit einer Active Directory-Domäne verknüpft ist, erstellt das Cmdlet eine Regel, indem der vom Administrator bereitgestellte Computername verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="5f803-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="5f803-118">Der Endbenutzer muss den Computernamen exakt so angeben, wie er in der Regel angezeigt wird, um sich erfolgreich mit diesem Computer zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="5f803-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="5f803-119">Wenn es in einem Netzwerk mehrere Computer mit dem gleichen Namen gibt, kann ein kurzer Name sich auf mehr als einen Computer beziehen.</span><span class="sxs-lookup"><span data-stu-id="5f803-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="5f803-120">Dies kann beim Herstellen einer Verbindung zu Mehrdeutigkeit führen.</span><span class="sxs-lookup"><span data-stu-id="5f803-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="5f803-121">Wenn zum Beispiel eine Regel für den Arbeitsgruppencomputer „*Server1* besteht, und ein neuer Computer namens *server1.contoso.com* mit dem Netzwerk verknüpft wird, ist die Überprüfung mithilfe der Autorisierungsregeln erfolgreich. Windows PowerShell Web Access versucht dann, eine Verbindung zu dem Computer namens „*Server1*“ herzustellen.</span><span class="sxs-lookup"><span data-stu-id="5f803-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="5f803-122">Es kann nicht garantiert werden, dass die Verbindung mit dem angegebenen Arbeitsgruppencomputer hergestellt werden kann. Der Versuch kann entweder für die Arbeitsgruppe oder den Domänencomputer namens „*Server1*“ unternommen werden.</span><span class="sxs-lookup"><span data-stu-id="5f803-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="5f803-123">Es wird empfohlen, dass Sie, wann immer es möglich ist, beim Erstellen einer Autorisierungsregel den FQDN für den Zielcomputer verwenden, um die Mehrdeutigkeit zu reduzieren.</span><span class="sxs-lookup"><span data-stu-id="5f803-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="5f803-124">Die Autorisierungsregeln werten die primären Anmeldeinformationen des Windows PowerShell Web Access-Benutzers aus, nicht die alternativen Anmeldeinformationen (der zweite Satz von Anmeldeinformationen, der im Abschnitt **Optionale Verbindungseinstellungen** der Anmeldeseite gefunden werden kann).</span><span class="sxs-lookup"><span data-stu-id="5f803-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="5f803-125">Ein Beispiel hierfür finden Sie unter Beispiel 6.</span><span class="sxs-lookup"><span data-stu-id="5f803-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="5f803-126">Parameter</span><span class="sxs-lookup"><span data-stu-id="5f803-126">Parameters</span></span>

### <a name="-computergroupname-string"></a><span data-ttu-id="5f803-127">-ComputerGroupName \<Zeichenfolge\></span><span class="sxs-lookup"><span data-stu-id="5f803-127">-ComputerGroupName \<String\></span></span>

<span data-ttu-id="5f803-128">Gibt den Namen einer Computergruppe in Active Directory Domain Services (AD DS) oder von lokalen Gruppen, denen diese Regel Zugriff gewährt, an.</span><span class="sxs-lookup"><span data-stu-id="5f803-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="5f803-129">Aliase</span><span class="sxs-lookup"><span data-stu-id="5f803-129">Aliases</span></span>                              | <span data-ttu-id="5f803-130">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-130">none</span></span>                                 |
| <span data-ttu-id="5f803-131">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="5f803-131">Required?</span></span>                            | <span data-ttu-id="5f803-132">wahr</span><span class="sxs-lookup"><span data-stu-id="5f803-132">true</span></span>                                 |
| <span data-ttu-id="5f803-133">Position?</span><span class="sxs-lookup"><span data-stu-id="5f803-133">Position?</span></span>                            | <span data-ttu-id="5f803-134">benannt</span><span class="sxs-lookup"><span data-stu-id="5f803-134">named</span></span>                                |
| <span data-ttu-id="5f803-135">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f803-135">Default Value</span></span>                        | <span data-ttu-id="5f803-136">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-136">none</span></span>                                 |
| <span data-ttu-id="5f803-137">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5f803-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="5f803-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="5f803-139">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5f803-140">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-140">false</span></span>                                |

### <a name="-computername-string"></a><span data-ttu-id="5f803-141">-ComputerName \<String\></span><span class="sxs-lookup"><span data-stu-id="5f803-141">-ComputerName \<String\></span></span>

<span data-ttu-id="5f803-142">Gibt den Namen des Computers an, dem diese Regel Zugriff gewährt.</span><span class="sxs-lookup"><span data-stu-id="5f803-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="5f803-143">Aliase</span><span class="sxs-lookup"><span data-stu-id="5f803-143">Aliases</span></span>                              | <span data-ttu-id="5f803-144">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-144">none</span></span>                                 |
| <span data-ttu-id="5f803-145">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="5f803-145">Required?</span></span>                            | <span data-ttu-id="5f803-146">wahr</span><span class="sxs-lookup"><span data-stu-id="5f803-146">true</span></span>                                 |
| <span data-ttu-id="5f803-147">Position?</span><span class="sxs-lookup"><span data-stu-id="5f803-147">Position?</span></span>                            | <span data-ttu-id="5f803-148">benannt</span><span class="sxs-lookup"><span data-stu-id="5f803-148">named</span></span>                                |
| <span data-ttu-id="5f803-149">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f803-149">Default Value</span></span>                        | <span data-ttu-id="5f803-150">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-150">none</span></span>                                 |
| <span data-ttu-id="5f803-151">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5f803-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="5f803-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="5f803-153">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5f803-154">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-154">false</span></span>                                |

### <a name="-configurationname-string"></a><span data-ttu-id="5f803-155">-ConfigurationName \<String\></span><span class="sxs-lookup"><span data-stu-id="5f803-155">-ConfigurationName \<String\></span></span>

<span data-ttu-id="5f803-156">Gibt den Namen einer Windows PowerShell-Sitzungskonfiguration (auch als Runspaces bezeichnet) an, der diese Regel Zugriff gewährt.</span><span class="sxs-lookup"><span data-stu-id="5f803-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="5f803-157">Aliase</span><span class="sxs-lookup"><span data-stu-id="5f803-157">Aliases</span></span>                              | <span data-ttu-id="5f803-158">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-158">none</span></span>                                 |
| <span data-ttu-id="5f803-159">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="5f803-159">Required?</span></span>                            | <span data-ttu-id="5f803-160">wahr</span><span class="sxs-lookup"><span data-stu-id="5f803-160">true</span></span>                                 |
| <span data-ttu-id="5f803-161">Position?</span><span class="sxs-lookup"><span data-stu-id="5f803-161">Position?</span></span>                            | <span data-ttu-id="5f803-162">benannt</span><span class="sxs-lookup"><span data-stu-id="5f803-162">named</span></span>                                |
| <span data-ttu-id="5f803-163">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f803-163">Default Value</span></span>                        | <span data-ttu-id="5f803-164">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-164">none</span></span>                                 |
| <span data-ttu-id="5f803-165">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5f803-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="5f803-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="5f803-167">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5f803-168">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-168">false</span></span>                                |

### <a name="-credential--pscredential"></a><span data-ttu-id="5f803-169">-Credential \<PSCredential\></span><span class="sxs-lookup"><span data-stu-id="5f803-169">-Credential  \<PSCredential\></span></span>

<span data-ttu-id="5f803-170">Gibt ein **PSCredential**-Objekt für ein Benutzerkonto an, das Sie zum Ändern der Windows PowerShell Web Access-Autorisierungsregeln verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="5f803-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="5f803-171">Wenn Sie diesen Parameter nicht hinzufügen, verwendet das Cmdlet das aktuell angemeldete Benutzerkonto.</span><span class="sxs-lookup"><span data-stu-id="5f803-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="5f803-172">Führen Sie zum Abrufen eines **PSCredential**-Objekts, das zum Hinzufügen von Autorisierungsregeln im Remotemodus erforderlich ist, das Cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) aus.</span><span class="sxs-lookup"><span data-stu-id="5f803-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="5f803-173">Aliase</span><span class="sxs-lookup"><span data-stu-id="5f803-173">Aliases</span></span>                              | <span data-ttu-id="5f803-174">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-174">none</span></span>                                 |
| <span data-ttu-id="5f803-175">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="5f803-175">Required?</span></span>                            | <span data-ttu-id="5f803-176">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-176">false</span></span>                                |
| <span data-ttu-id="5f803-177">Position?</span><span class="sxs-lookup"><span data-stu-id="5f803-177">Position?</span></span>                            | <span data-ttu-id="5f803-178">benannt</span><span class="sxs-lookup"><span data-stu-id="5f803-178">named</span></span>                                |
| <span data-ttu-id="5f803-179">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f803-179">Default Value</span></span>                        | <span data-ttu-id="5f803-180">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-180">none</span></span>                                 |
| <span data-ttu-id="5f803-181">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5f803-182">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-182">false</span></span>                                |
| <span data-ttu-id="5f803-183">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5f803-184">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="5f803-185">-Force</span><span class="sxs-lookup"><span data-stu-id="5f803-185">-Force</span></span>

<span data-ttu-id="5f803-186">Erzwingt die Ausführung des Befehls ohne Aufforderung zur Bestätigung durch den Benutzer.</span><span class="sxs-lookup"><span data-stu-id="5f803-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="5f803-187">Zusätzlich werden Sie zu einer Bestätigung aufgefordert, wenn Sie einen einfachen oder kurzen Computernamen eingeben (z.B. ein Name, der kein Domänenname und nicht vollqualifiziert ist).</span><span class="sxs-lookup"><span data-stu-id="5f803-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="5f803-188">Die Bestätigung ist aus Sicherheitsgründen erforderlich. Dadurch können Sie einen einfachen Namen zum Hinzufügen eines Computers nur verwenden, wenn der Computer sich in einer Arbeitsgruppe befindet.</span><span class="sxs-lookup"><span data-stu-id="5f803-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="5f803-189">Aliase</span><span class="sxs-lookup"><span data-stu-id="5f803-189">Aliases</span></span>                              | <span data-ttu-id="5f803-190">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-190">none</span></span>                                 |
| <span data-ttu-id="5f803-191">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="5f803-191">Required?</span></span>                            | <span data-ttu-id="5f803-192">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-192">false</span></span>                                |
| <span data-ttu-id="5f803-193">Position?</span><span class="sxs-lookup"><span data-stu-id="5f803-193">Position?</span></span>                            | <span data-ttu-id="5f803-194">benannt</span><span class="sxs-lookup"><span data-stu-id="5f803-194">named</span></span>                                |
| <span data-ttu-id="5f803-195">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f803-195">Default Value</span></span>                        | <span data-ttu-id="5f803-196">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-196">none</span></span>                                 |
| <span data-ttu-id="5f803-197">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5f803-198">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-198">false</span></span>                                |
| <span data-ttu-id="5f803-199">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5f803-200">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-200">false</span></span>                                |

### <a name="-rulename-string"></a><span data-ttu-id="5f803-201">-RuleName \<Zeichenfolge\></span><span class="sxs-lookup"><span data-stu-id="5f803-201">-RuleName \<String\></span></span>

<span data-ttu-id="5f803-202">Gibt den Anzeigenamen für diese Regel an.</span><span class="sxs-lookup"><span data-stu-id="5f803-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="5f803-203">Aliase</span><span class="sxs-lookup"><span data-stu-id="5f803-203">Aliases</span></span>                              | <span data-ttu-id="5f803-204">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-204">none</span></span>                                 |
| <span data-ttu-id="5f803-205">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="5f803-205">Required?</span></span>                            | <span data-ttu-id="5f803-206">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-206">false</span></span>                                |
| <span data-ttu-id="5f803-207">Position?</span><span class="sxs-lookup"><span data-stu-id="5f803-207">Position?</span></span>                            | <span data-ttu-id="5f803-208">benannt</span><span class="sxs-lookup"><span data-stu-id="5f803-208">named</span></span>                                |
| <span data-ttu-id="5f803-209">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f803-209">Default Value</span></span>                        | <span data-ttu-id="5f803-210">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-210">none</span></span>                                 |
| <span data-ttu-id="5f803-211">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5f803-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="5f803-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="5f803-213">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5f803-214">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-214">false</span></span>                                |

### <a name="-usergroupname-string"></a><span data-ttu-id="5f803-215">-UserGroupName \<Zeichenfolge\[\]\></span><span class="sxs-lookup"><span data-stu-id="5f803-215">-UserGroupName \<String\[\]\></span></span>

<span data-ttu-id="5f803-216">Gibt den Namen für eine oder mehrere Benutzergruppen in AD DS oder für lokale Gruppen, denen diese Regel Zugriff gewährt, an.</span><span class="sxs-lookup"><span data-stu-id="5f803-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="5f803-217">Aliase</span><span class="sxs-lookup"><span data-stu-id="5f803-217">Aliases</span></span>                              | <span data-ttu-id="5f803-218">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-218">none</span></span>                                 |
| <span data-ttu-id="5f803-219">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="5f803-219">Required?</span></span>                            | <span data-ttu-id="5f803-220">wahr</span><span class="sxs-lookup"><span data-stu-id="5f803-220">true</span></span>                                 |
| <span data-ttu-id="5f803-221">Position?</span><span class="sxs-lookup"><span data-stu-id="5f803-221">Position?</span></span>                            | <span data-ttu-id="5f803-222">benannt</span><span class="sxs-lookup"><span data-stu-id="5f803-222">named</span></span>                                |
| <span data-ttu-id="5f803-223">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f803-223">Default Value</span></span>                        | <span data-ttu-id="5f803-224">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-224">none</span></span>                                 |
| <span data-ttu-id="5f803-225">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5f803-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="5f803-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="5f803-227">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5f803-228">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-228">false</span></span>                                |

### <a name="-username-string"></a><span data-ttu-id="5f803-229">-UserName \<Zeichenfolge\[\]\></span><span class="sxs-lookup"><span data-stu-id="5f803-229">-UserName \<String\[\]\></span></span>

<span data-ttu-id="5f803-230">Gibt den Namen von einem oder mehreren Benutzern an, denen diese Regel Zugriff gewährt.</span><span class="sxs-lookup"><span data-stu-id="5f803-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="5f803-231">Beim Benutzernamen kann es sich um ein lokales Benutzerkonto auf dem Gatewaycomputer oder um einen Benutzer in AD DS handeln.</span><span class="sxs-lookup"><span data-stu-id="5f803-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="5f803-232">Das Format ist `domain\user` oder `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="5f803-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="5f803-233">Aliase</span><span class="sxs-lookup"><span data-stu-id="5f803-233">Aliases</span></span>                              | <span data-ttu-id="5f803-234">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-234">none</span></span>                                 |
| <span data-ttu-id="5f803-235">Erforderlich?</span><span class="sxs-lookup"><span data-stu-id="5f803-235">Required?</span></span>                            | <span data-ttu-id="5f803-236">wahr</span><span class="sxs-lookup"><span data-stu-id="5f803-236">true</span></span>                                 |
| <span data-ttu-id="5f803-237">Position?</span><span class="sxs-lookup"><span data-stu-id="5f803-237">Position?</span></span>                            | <span data-ttu-id="5f803-238">1</span><span class="sxs-lookup"><span data-stu-id="5f803-238">1</span></span>                                    |
| <span data-ttu-id="5f803-239">Standardwert</span><span class="sxs-lookup"><span data-stu-id="5f803-239">Default Value</span></span>                        | <span data-ttu-id="5f803-240">keine</span><span class="sxs-lookup"><span data-stu-id="5f803-240">none</span></span>                                 |
| <span data-ttu-id="5f803-241">Pipelineeingaben akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="5f803-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="5f803-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="5f803-243">Platzhalterzeichen akzeptieren?</span><span class="sxs-lookup"><span data-stu-id="5f803-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="5f803-244">falsch</span><span class="sxs-lookup"><span data-stu-id="5f803-244">false</span></span>                                |

###  <a name="commonparameters"></a><span data-ttu-id="5f803-245">\<CommonParameters\></span><span class="sxs-lookup"><span data-stu-id="5f803-245">\<CommonParameters\></span></span>

<span data-ttu-id="5f803-246">Dieses Cmdlet unterstützt die folgenden allgemeinen Parameter: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer und -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="5f803-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="5f803-247">Weitere Informationen finden Sie unter [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="5f803-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="5f803-248">EINGABEN</span><span class="sxs-lookup"><span data-stu-id="5f803-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="5f803-249">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="5f803-249">String</span></span>

<span data-ttu-id="5f803-250">Dieses Cmdlet akzeptiert eine Zeichenfolge oder ein Array von Zeichenfolgen als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="5f803-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="5f803-251">String\[\]</span><span class="sxs-lookup"><span data-stu-id="5f803-251">String\[\]</span></span>

<span data-ttu-id="5f803-252">Dieses Cmdlet akzeptiert eine Zeichenfolge oder ein Array von Zeichenfolgen als Eingabe.</span><span class="sxs-lookup"><span data-stu-id="5f803-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="5f803-253">Ausgaben</span><span class="sxs-lookup"><span data-stu-id="5f803-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="5f803-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="5f803-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="5f803-255">Dieses Cmdlet gibt ein Objekt der Autorisierungsregel zurück.</span><span class="sxs-lookup"><span data-stu-id="5f803-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="5f803-256">BEISPIELE</span><span class="sxs-lookup"><span data-stu-id="5f803-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="5f803-257">BEISPIEL 1</span><span class="sxs-lookup"><span data-stu-id="5f803-257">EXAMPLE 1</span></span>

<span data-ttu-id="5f803-258">In diesem Beispiel wird Zugriff auf die Sitzungskonfiguration _PSWAEndpoint_, ein eingeschränkter Runspace, auf _srv2_ für Benutzer der Gruppe _SMAdmins_ gewährt.</span><span class="sxs-lookup"><span data-stu-id="5f803-258">This example grants access to the session configuration _PSWAEndpoint_, a restricted runspace, on _srv2_ for users in the _SMAdmins_ group.</span></span>

> [!NOTE]
> <span data-ttu-id="5f803-259">Der Computername muss ein voll qualifizierter Domänenname (FQDN) sein.</span><span class="sxs-lookup"><span data-stu-id="5f803-259">The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="5f803-260">Administratoren definieren eine eingeschränkte Sitzungskonfiguration bzw. einen Runspace. Dabei handelt es sich um einen begrenzten Bereich von Cmdlets und Aufgaben, die die Endbenutzer ausführen können.</span><span class="sxs-lookup"><span data-stu-id="5f803-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="5f803-261">Das Definieren eines eingeschränkten Runspaces kann verhindern, dass Benutzer auf andere Computer zugreifen, die sich nicht im zugelassenen Windows PowerShell®-Runspace befinden. Dadurch wird eine sicherere Verbindung ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="5f803-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="5f803-262">Weitere Informationen finden Sie unter [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) oder [Install and Use Windows PowerShell Web Access (Installieren und Verwenden von Windows PowerShell Web Access)](../install-and-use-windows-powershell-web-access.md).</span><span class="sxs-lookup"><span data-stu-id="5f803-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="5f803-263">BEISPIEL 2</span><span class="sxs-lookup"><span data-stu-id="5f803-263">EXAMPLE 2</span></span>

<span data-ttu-id="5f803-264">In diesem Beispiel wird Zugriff auf die Windows PowerShell-Standardsitzungskonfiguration, `Microsoft.PowerShell`, auf *srv2* für Benutzer in `contoso\user1`, `contoso\user2` und `contoso\user3` gewährt.</span><span class="sxs-lookup"><span data-stu-id="5f803-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named `contoso\user1`, `contoso\user2`, and `contoso\user3`.</span></span> <span data-ttu-id="5f803-265">Dieses Cmdlet erstellt drei Regeln (eine pro Person).</span><span class="sxs-lookup"><span data-stu-id="5f803-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="5f803-266">BEISPIEL 3</span><span class="sxs-lookup"><span data-stu-id="5f803-266">EXAMPLE 3</span></span>

<span data-ttu-id="5f803-267">In diesem Beispiel wird veranschaulicht, wie Benutzernamenwerte über die Pipeline eingegeben werden.</span><span class="sxs-lookup"><span data-stu-id="5f803-267">This example illustrates how to input user name values via the pipeline.</span></span>

```powershell
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="5f803-268">BEISPIEL 4</span><span class="sxs-lookup"><span data-stu-id="5f803-268">EXAMPLE 4</span></span>

<span data-ttu-id="5f803-269">In diesem Beispiel wird veranschaulicht, wie alle Parameter Werte aus der Pipeline nach Eigenschaftsname annehmen.</span><span class="sxs-lookup"><span data-stu-id="5f803-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="5f803-270">BEISPIEL 5</span><span class="sxs-lookup"><span data-stu-id="5f803-270">EXAMPLE 5</span></span>

<span data-ttu-id="5f803-271">In diesem Beispiel wird eine Regel hinzugefügt, um dem lokalen Benutzer `PswaServer\ChrisLocal` Zugriff auf den Server namens **srv1.contoso.com** zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="5f803-271">This example adds a rule to allow the local user named `PswaServer\ChrisLocal` access to the server named **srv1.contoso.com**.</span></span>

<span data-ttu-id="5f803-272">Dieses Beispiel veranschaulicht ein Szenario, in dem das Gateway sich in einer Arbeitsgruppe und der Zielcomputer sich in einer Domäne befindet.</span><span class="sxs-lookup"><span data-stu-id="5f803-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="5f803-273">Die Autorisierungsregel gilt für die lokalen Benutzer auf dem Gateway.</span><span class="sxs-lookup"><span data-stu-id="5f803-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="5f803-274">Der Benutzer muss einen zweiten Satz von Anmeldeinformationen im Bereich **Optionale Verbindungseinstellungen** auf der Windows PowerShell Web Access-Anmeldeseite angeben, um sich erfolgreich zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="5f803-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="5f803-275">Der Gatewayserver verwendet den zusätzlichen Satz von Anmeldeinformationen, um den Benutzer auf dem Zielcomputer zu authentifizieren, einem Server namens *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="5f803-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````powershell
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="5f803-276">BEISPIEL 6</span><span class="sxs-lookup"><span data-stu-id="5f803-276">EXAMPLE 6</span></span>

<span data-ttu-id="5f803-277">In diesem Beispiel wird allen Endbenutzern Zugriff auf alle Endpunkte aller Computer gewährt.</span><span class="sxs-lookup"><span data-stu-id="5f803-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="5f803-278">Dadurch werden die Autorisierungsregeln deaktiviert.</span><span class="sxs-lookup"><span data-stu-id="5f803-278">This essentially turns off authorization rules.</span></span>

> [!NOTE]
> <span data-ttu-id="5f803-279">Das Verwenden des Platzhalterzeichens `*` wird für sicherheitsrelevante Bereitstellungen nicht empfohlen. Es sollte nur für Testumgebungen in Betracht gezogen oder für Bereitstellungen verwendet werden, bei denen die Sicherheit gelockert werden kann.</span><span class="sxs-lookup"><span data-stu-id="5f803-279">Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="5f803-280">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5f803-280">See Also</span></span>

<span data-ttu-id="5f803-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="5f803-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>

<span data-ttu-id="5f803-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="5f803-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>

<span data-ttu-id="5f803-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="5f803-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>

<span data-ttu-id="5f803-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="5f803-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>

[<span data-ttu-id="5f803-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="5f803-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)

[<span data-ttu-id="5f803-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="5f803-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)

[<span data-ttu-id="5f803-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="5f803-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)