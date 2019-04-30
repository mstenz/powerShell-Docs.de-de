---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: DSC-Ressource „Registry“
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076955"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="b8ea4-103">DSC-Ressource „Registry“</span><span class="sxs-lookup"><span data-stu-id="b8ea4-103">DSC Registry Resource</span></span>

<span data-ttu-id="b8ea4-104">_Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="b8ea4-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="b8ea4-105">Die Ressource **Registry** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Registrierungsschlüsseln und -werten auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="b8ea4-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b8ea4-106">Syntax</span></span>

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

## <a name="properties"></a><span data-ttu-id="b8ea4-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="b8ea4-107">Properties</span></span>

| <span data-ttu-id="b8ea4-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="b8ea4-108">Property</span></span> | <span data-ttu-id="b8ea4-109">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b8ea4-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="b8ea4-110">Key</span><span class="sxs-lookup"><span data-stu-id="b8ea4-110">Key</span></span>| <span data-ttu-id="b8ea4-111">Gibt den Pfad des Registrierungsschlüssels an, für den Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="b8ea4-112">Dieser Pfad muss die Struktur enthalten.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-112">This path must include the hive.</span></span>|
| <span data-ttu-id="b8ea4-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="b8ea4-113">ValueName</span></span>| <span data-ttu-id="b8ea4-114">Gibt den Namen des Registrierungswerts an.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="b8ea4-115">Um einen Registrierungsschlüssel hinzuzufügen oder zu entfernen, geben Sie diese Eigenschaft als leere Zeichenfolge ohne Angabe von „ValueType“ oder „ValueData“ an.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-115">To add or remove a registry key, specify this property as an empty string without specifying ValueType or ValueData.</span></span> <span data-ttu-id="b8ea4-116">Um den Standardwert eines Registrierungsschlüssels zu ändern oder zu entfernen, geben Sie diese Eigenschaft als leere Zeichenfolge an und legen gleichzeitig „ValueType“ oder „ValueData“ fest.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying ValueType or ValueData.</span></span>|
| <span data-ttu-id="b8ea4-117">Ensure</span><span class="sxs-lookup"><span data-stu-id="b8ea4-117">Ensure</span></span>| <span data-ttu-id="b8ea4-118">Gibt an, ob Schlüssel und Wert vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-118">Indicates if the key and value exist.</span></span> <span data-ttu-id="b8ea4-119">Um dies sicherzustellen, legen Sie diese Eigenschaft auf „Present“ fest.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-119">To ensure that they do, set this property to "Present".</span></span> <span data-ttu-id="b8ea4-120">Um sicherzustellen, dass sie nicht vorhanden sind, legen Sie die Eigenschaft auf „Absent“ fest.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-120">To ensure that they do not exist, set the property to "Absent".</span></span> <span data-ttu-id="b8ea4-121">Der Standardwert ist „Present“.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-121">The default value is "Present".</span></span>|
| <span data-ttu-id="b8ea4-122">Force</span><span class="sxs-lookup"><span data-stu-id="b8ea4-122">Force</span></span>| <span data-ttu-id="b8ea4-123">Wenn der angegebene Registrierungsschlüssel vorhanden ist, wird dieser von **Force** mit dem neuen Wert überschrieben.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-123">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="b8ea4-124">Beim Löschen eines Registrierungsschlüssels mit Unterschlüsseln muss dieser Wert **$true** lauten.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-124">If deleting a registry key with subkeys, this needs to be **$true**</span></span> |
| <span data-ttu-id="b8ea4-125">Hex</span><span class="sxs-lookup"><span data-stu-id="b8ea4-125">Hex</span></span>| <span data-ttu-id="b8ea4-126">Gibt an, ob Daten im Hexadezimalformat ausgedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-126">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="b8ea4-127">Falls angegeben, werden die DWORD/QWORD-Wertdaten im Hexadezimalformat angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-127">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="b8ea4-128">Gilt nicht für andere Typen.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-128">Not valid for other types.</span></span> <span data-ttu-id="b8ea4-129">Der Standardwert ist **$false**.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-129">The default value is **$false**.</span></span>|
| <span data-ttu-id="b8ea4-130">DependsOn</span><span class="sxs-lookup"><span data-stu-id="b8ea4-130">DependsOn</span></span>| <span data-ttu-id="b8ea4-131">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-131">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="b8ea4-132">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-132">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="b8ea4-133">ValueData</span><span class="sxs-lookup"><span data-stu-id="b8ea4-133">ValueData</span></span>| <span data-ttu-id="b8ea4-134">Die Daten des Registrierungswerts.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-134">The data for the registry value.</span></span>|
| <span data-ttu-id="b8ea4-135">ValueType</span><span class="sxs-lookup"><span data-stu-id="b8ea4-135">ValueType</span></span>| <span data-ttu-id="b8ea4-136">Gibt den Typ des Werts an.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-136">Indicates the type of the value.</span></span> <span data-ttu-id="b8ea4-137">Die unterstützten Typen sind: Zeichenfolge (REG_SZ), Binär (REG-BINARY), Dword 32-Bit (REG_DWORD), Qword 64-Bit (REG_QWORD), mehrteilige Zeichenfolge (REG_MULTI_SZ), erweiterbare Zeichenfolge (REG_EXPAND_SZ)</span><span class="sxs-lookup"><span data-stu-id="b8ea4-137">The supported types are: String (REG_SZ), Binary (REG-BINARY), Dword 32-bit (REG_DWORD), Qword 64-bit (REG_QWORD), Multi-string (REG_MULTI_SZ), Expandable string (REG_EXPAND_SZ)</span></span> |

## <a name="example"></a><span data-ttu-id="b8ea4-138">Beispiel</span><span class="sxs-lookup"><span data-stu-id="b8ea4-138">Example</span></span>

<span data-ttu-id="b8ea4-139">In diesem Beispiel wird sichergestellt, dass ein Schlüssel mit dem Namen „ExampleKey“ in der Struktur **HKEY\_LOCAL\_MACHINE** vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-139">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

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

> [!NOTE]
> <span data-ttu-id="b8ea4-140">Das Ändern einer Registrierungseinstellung in der Struktur `HKEY\CURRENT\USER` erfordert, dass die Konfiguration mit Benutzeranmeldeinformationen anstatt mit Anmeldeinformationen des Systems ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-140">Changing a registry setting in the `HKEY\CURRENT\USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="b8ea4-141">Sie können die **PsDscRunAsCredential**-Eigenschaft verwenden, um die Benutzeranmeldeinformationen für die Konfiguration anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b8ea4-141">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="b8ea4-142">Ein Beispiel finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](../../../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="b8ea4-142">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>
