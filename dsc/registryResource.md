---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „Registry“
ms.openlocfilehash: 8819b3704fa1a61d2be5ce11c974542f48177e09
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="0c36c-103">DSC-Ressource „Registry“</span><span class="sxs-lookup"><span data-stu-id="0c36c-103">DSC Registry Resource</span></span>

> <span data-ttu-id="0c36c-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0c36c-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0c36c-105">Die Ressource **Registry** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Registrierungsschlüsseln und -werten auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="0c36c-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="0c36c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c36c-106">Syntax</span></span>

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a><span data-ttu-id="0c36c-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="0c36c-107">Properties</span></span>
|  <span data-ttu-id="0c36c-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="0c36c-108">Property</span></span>  |  <span data-ttu-id="0c36c-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0c36c-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="0c36c-110">Key</span><span class="sxs-lookup"><span data-stu-id="0c36c-110">Key</span></span>| <span data-ttu-id="0c36c-111">Gibt den Pfad des Registrierungsschlüssels an, für den Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="0c36c-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="0c36c-112">Dieser Pfad muss die Struktur enthalten.</span><span class="sxs-lookup"><span data-stu-id="0c36c-112">This path must include the hive.</span></span>|
| <span data-ttu-id="0c36c-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="0c36c-113">ValueName</span></span>| <span data-ttu-id="0c36c-114">Gibt den Namen des Registrierungswerts an.</span><span class="sxs-lookup"><span data-stu-id="0c36c-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="0c36c-115">Um einen Registrierungsschlüssel hinzuzufügen oder zu entfernen, geben Sie diese Eigenschaft als leere Zeichenfolge ohne Angabe von „ValueType“ oder „ValueData“ an.</span><span class="sxs-lookup"><span data-stu-id="0c36c-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="0c36c-116">Um den Standardwert eines Registrierungsschlüssels zu ändern oder zu entfernen, geben Sie diese Eigenschaft als leere Zeichenfolge an und legen gleichzeitig „ValueType“ oder „ValueData“ fest.</span><span class="sxs-lookup"><span data-stu-id="0c36c-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="0c36c-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="0c36c-117">Ensure</span></span>| <span data-ttu-id="0c36c-118">Gibt an, ob Schlüssel und Wert vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="0c36c-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="0c36c-119">Um dies sicherzustellen, legen Sie diese Eigenschaft auf „Present“ fest.</span><span class="sxs-lookup"><span data-stu-id="0c36c-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="0c36c-120">Um sicherzustellen, dass sie nicht vorhanden sind, legen Sie die Eigenschaft auf „Absent“ fest.</span><span class="sxs-lookup"><span data-stu-id="0c36c-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="0c36c-121">Der Standardwert ist „Present“.</span><span class="sxs-lookup"><span data-stu-id="0c36c-121">The default value is "Present".</span></span>|
| <span data-ttu-id="0c36c-122">Force</span><span class="sxs-lookup"><span data-stu-id="0c36c-122">Force</span></span>| <span data-ttu-id="0c36c-123">Wenn der angegebene Registrierungsschlüssel vorhanden ist, wird dieser von __Force__ mit dem neuen Wert überschrieben.</span><span class="sxs-lookup"><span data-stu-id="0c36c-123">If the specified registry key is present, __Force__ overwrites it with the new value.</span></span> <span data-ttu-id="0c36c-124">Beim Löschen eines Registrierungsschlüssels mit Unterschlüsseln muss dieser Wert __$true__ lauten.</span><span class="sxs-lookup"><span data-stu-id="0c36c-124">If deleting a registry key with subkeys, this needs to be __$true__</span></span>|
| <span data-ttu-id="0c36c-125">Hex</span><span class="sxs-lookup"><span data-stu-id="0c36c-125">Hex</span></span>| <span data-ttu-id="0c36c-126">Gibt an, ob Daten im Hexadezimalformat ausgedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="0c36c-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="0c36c-127">Falls angegeben, werden die DWORD/QWORD-Wertdaten im Hexadezimalformat angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0c36c-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="0c36c-128">Gilt nicht für andere Typen.</span><span class="sxs-lookup"><span data-stu-id="0c36c-128">Not valid for other types.</span></span> <span data-ttu-id="0c36c-129">Der Standardwert ist __$false__.</span><span class="sxs-lookup"><span data-stu-id="0c36c-129">The default value is __$false__.</span></span>|
| <span data-ttu-id="0c36c-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="0c36c-130">DependsOn</span></span>| <span data-ttu-id="0c36c-131">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="0c36c-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="0c36c-132">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, __ResourceName__ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="0c36c-132">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="0c36c-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="0c36c-133">ValueData</span></span>| <span data-ttu-id="0c36c-134">Die Daten des Registrierungswerts.</span><span class="sxs-lookup"><span data-stu-id="0c36c-134">The data for the registry value.</span></span>|
| <span data-ttu-id="0c36c-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="0c36c-135">ValueType</span></span>| <span data-ttu-id="0c36c-136">Gibt den Typ des Werts an.</span><span class="sxs-lookup"><span data-stu-id="0c36c-136">Indicates the type of the value.</span></span> <span data-ttu-id="0c36c-137">Die unterstützten Typen sind:</span><span class="sxs-lookup"><span data-stu-id="0c36c-137">The supported types are:</span></span>
<ul><li><span data-ttu-id="0c36c-138">Zeichenfolge (REG_SZ)</span><span class="sxs-lookup"><span data-stu-id="0c36c-138">String (REG_SZ)</span></span></li>


<li><span data-ttu-id="0c36c-139">Binär (REG-BINARY)</span><span class="sxs-lookup"><span data-stu-id="0c36c-139">Binary (REG-BINARY)</span></span></li>


<li><span data-ttu-id="0c36c-140">Dword 32-Bit (REG_DWORD)</span><span class="sxs-lookup"><span data-stu-id="0c36c-140">Dword 32-bit (REG_DWORD)</span></span></li>


<li><span data-ttu-id="0c36c-141">Qword 64-Bit (REG_QWORD)</span><span class="sxs-lookup"><span data-stu-id="0c36c-141">Qword 64-bit (REG_QWORD)</span></span></li>


<li><span data-ttu-id="0c36c-142">Mehrteilige Zeichenfolge (REG_MULTI_SZ)</span><span class="sxs-lookup"><span data-stu-id="0c36c-142">Multi-string (REG_MULTI_SZ)</span></span></li>


<li><span data-ttu-id="0c36c-143">Erweiterbare Zeichenfolge (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="0c36c-143">Expandable string (REG_EXPAND_SZ)</span></span></li></ul>

## <a name="example"></a><span data-ttu-id="0c36c-144">Beispiel</span><span class="sxs-lookup"><span data-stu-id="0c36c-144">Example</span></span>
<span data-ttu-id="0c36c-145">In diesem Beispiel wird sichergestellt, dass ein Schlüssel mit dem Namen „ExampleKey“ in der Struktur **HKEY\_LOCAL\_MACHINE** vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="0c36c-145">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>
```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

><span data-ttu-id="0c36c-146">**Hinweis:** Das Ändern einer Einstellung in der Registrierungseinstellung in der Struktur **HKEY\_CURRENT\_USER** erfordert, dass die Konfiguration mit Benutzeranmeldeinformationen anstatt mit Anmeldeinformationen des Systems ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0c36c-146">**Note:** Changing a registry setting in the **HKEY\_CURRENT\_USER** hive requires that the configuration runs with user credentials, rather than as the system.</span></span>
><span data-ttu-id="0c36c-147">Sie können die **PsDscRunAsCredential**-Eigenschaft verwenden, um die Benutzeranmeldeinformationen für die Konfiguration anzugeben.</span><span class="sxs-lookup"><span data-stu-id="0c36c-147">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="0c36c-148">Ein Beispiel finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="0c36c-148">For an example, see [Running DSC with user credentials](runAsUser.md)</span></span>
