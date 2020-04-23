---
ms.date: 09/20/2019
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: DSC-Ressource „Registry“
ms.openlocfilehash: be2f9134368784ad2d208362104ce046c49492e0
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953077"
---
# <a name="dsc-registry-resource"></a><span data-ttu-id="2a6d1-103">DSC-Ressource „Registry“</span><span class="sxs-lookup"><span data-stu-id="2a6d1-103">DSC Registry Resource</span></span>

> <span data-ttu-id="2a6d1-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="2a6d1-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="2a6d1-105">Die Ressource **Registry** in Windows PowerShell DSC bietet einen Mechanismus zum Verwalten von Registrierungsschlüsseln und -werten auf einem Zielknoten.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-105">The **Registry** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage registry keys and values on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a6d1-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a6d1-106">Syntax</span></span>

```Syntax
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Present | Absent }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="2a6d1-107">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="2a6d1-107">Properties</span></span>

|<span data-ttu-id="2a6d1-108">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="2a6d1-108">Property</span></span> |<span data-ttu-id="2a6d1-109">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="2a6d1-109">Description</span></span> |
|---|---|
|<span data-ttu-id="2a6d1-110">Schlüssel</span><span class="sxs-lookup"><span data-stu-id="2a6d1-110">Key</span></span> |<span data-ttu-id="2a6d1-111">Gibt den Pfad des Registrierungsschlüssels an, für den Sie einen bestimmten Zustand sicherstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-111">Indicates the path of the registry key for which you want to ensure a specific state.</span></span> <span data-ttu-id="2a6d1-112">Dieser Pfad muss die Struktur enthalten.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-112">This path must include the hive.</span></span> |
|<span data-ttu-id="2a6d1-113">ValueName</span><span class="sxs-lookup"><span data-stu-id="2a6d1-113">ValueName</span></span> |<span data-ttu-id="2a6d1-114">Gibt den Namen des Registrierungswerts an.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-114">Indicates the name of the registry value.</span></span> <span data-ttu-id="2a6d1-115">Um einen Registrierungsschlüssel hinzuzufügen oder zu entfernen, geben Sie diese Eigenschaft als leere Zeichenfolge ohne Angabe von **ValueType** oder **ValueData** an.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-115">To add or remove a registry key, specify this property as an empty string without specifying **ValueType** or **ValueData**.</span></span> <span data-ttu-id="2a6d1-116">Um den Standardwert eines Registrierungsschlüssels zu ändern oder zu entfernen, geben Sie diese Eigenschaft als leere Zeichenfolge an und legen gleichzeitig **ValueType** oder **ValueData** fest.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-116">To modify or remove the default value of a registry key, specify this property as an empty string while also specifying **ValueType** or **ValueData**.</span></span> |
|<span data-ttu-id="2a6d1-117">Force</span><span class="sxs-lookup"><span data-stu-id="2a6d1-117">Force</span></span> |<span data-ttu-id="2a6d1-118">Wenn der angegebene Registrierungsschlüssel vorhanden ist, wird dieser von **Force** mit dem neuen Wert überschrieben.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-118">If the specified registry key is present, **Force** overwrites it with the new value.</span></span> <span data-ttu-id="2a6d1-119">Beim Löschen eines Registrierungsschlüssels mit Unterschlüsseln muss dieser Wert `$true` lauten.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-119">If deleting a registry key with subkeys, this needs to be `$true`.</span></span> |
|<span data-ttu-id="2a6d1-120">Hex</span><span class="sxs-lookup"><span data-stu-id="2a6d1-120">Hex</span></span> |<span data-ttu-id="2a6d1-121">Gibt an, ob Daten im Hexadezimalformat ausgedrückt werden.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-121">Indicates if data will be expressed in hexadecimal format.</span></span> <span data-ttu-id="2a6d1-122">Falls angegeben, werden die DWORD/QWORD-Wertdaten im Hexadezimalformat angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-122">If specified, the DWORD/QWORD value data is presented in hexadecimal format.</span></span> <span data-ttu-id="2a6d1-123">Gilt nicht für andere Typen.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-123">Not valid for other types.</span></span> <span data-ttu-id="2a6d1-124">Standardwert: `$false`.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-124">The default value is `$false`.</span></span> |
|<span data-ttu-id="2a6d1-125">ValueData</span><span class="sxs-lookup"><span data-stu-id="2a6d1-125">ValueData</span></span> |<span data-ttu-id="2a6d1-126">Die Daten des Registrierungswerts.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-126">The data for the registry value.</span></span> |
|<span data-ttu-id="2a6d1-127">ValueType</span><span class="sxs-lookup"><span data-stu-id="2a6d1-127">ValueType</span></span> |<span data-ttu-id="2a6d1-128">Gibt den Typ des Werts an.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-128">Indicates the type of the value.</span></span> <span data-ttu-id="2a6d1-129">Die unterstützten Typen sind: **Zeichenfolge** (REG_SZ), **Binär** (REG-BINARY), **Dword** (32-Bit REG_DWORD), **Qword** (64-Bit REG_QWORD), **mehrteilige Zeichenfolge** (REG_MULTI_SZ), **erweiterbare Zeichenfolge** (REG_EXPAND_SZ).</span><span class="sxs-lookup"><span data-stu-id="2a6d1-129">The supported types are: **String** (REG_SZ), **Binary** (REG-BINARY), **Dword** (32-bit REG_DWORD), **Qword** (64-bit REG_QWORD), **MultiString** (REG_MULTI_SZ), **ExpandString** (REG_EXPAND_SZ).</span></span> |

## <a name="common-properties"></a><span data-ttu-id="2a6d1-130">Allgemeine Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="2a6d1-130">Common properties</span></span>

|<span data-ttu-id="2a6d1-131">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="2a6d1-131">Property</span></span> |<span data-ttu-id="2a6d1-132">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="2a6d1-132">Description</span></span> |
|---|---|
|<span data-ttu-id="2a6d1-133">DependsOn</span><span class="sxs-lookup"><span data-stu-id="2a6d1-133">DependsOn</span></span> |<span data-ttu-id="2a6d1-134">Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-134">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="2a6d1-135">Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ „ResourceType“ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-135">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="2a6d1-136">Ensure</span><span class="sxs-lookup"><span data-stu-id="2a6d1-136">Ensure</span></span> |<span data-ttu-id="2a6d1-137">Gibt an, ob Schlüssel und Wert vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-137">Indicates if the key and value exist.</span></span> <span data-ttu-id="2a6d1-138">Um dies sicherzustellen, legen Sie diese Eigenschaft auf **Present** fest.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-138">To ensure that they do, set this property to **Present**.</span></span> <span data-ttu-id="2a6d1-139">Um sicherzustellen, dass sie nicht vorhanden sind, legen Sie die Eigenschaft auf **Absent** fest.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-139">To ensure that they do not exist, set the property to **Absent**.</span></span> <span data-ttu-id="2a6d1-140">Der Standardwert ist **Present**.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-140">The default value is **Present**.</span></span> |
|<span data-ttu-id="2a6d1-141">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="2a6d1-141">PsDscRunAsCredential</span></span> |<span data-ttu-id="2a6d1-142">Legt die Anmeldeinformationen für die Ausführung der gesamten Ressource fest.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-142">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="2a6d1-143">Die allgemeine Eigenschaft **PsDscRunAsCredential** wurde in WMF 5.0 hinzugefügt, um das Ausführen einer beliebigen DSC-Ressource in Verbindung mit anderen Anmeldeinformationen zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-143">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="2a6d1-144">Weitere Informationen finden Sie unter [Use Credentials with DSC Resources](../../../configurations/runasuser.md) (Verwenden von Anmeldeinformationen mit DSC-Ressourcen).</span><span class="sxs-lookup"><span data-stu-id="2a6d1-144">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

## <a name="example"></a><span data-ttu-id="2a6d1-145">Beispiel</span><span class="sxs-lookup"><span data-stu-id="2a6d1-145">Example</span></span>

<span data-ttu-id="2a6d1-146">In diesem Beispiel wird sichergestellt, dass ein Schlüssel mit dem Namen „ExampleKey“ in der Struktur **HKEY\_LOCAL\_MACHINE** vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-146">This example ensures that a key named "ExampleKey" is present in the **HKEY\_LOCAL\_MACHINE** hive.</span></span>

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
> <span data-ttu-id="2a6d1-147">Das Ändern einer Registrierungseinstellung in der Struktur `HKEY_CURRENT_USER` erfordert, dass die Konfiguration mit Benutzeranmeldeinformationen anstatt mit Anmeldeinformationen des Systems ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-147">Changing a registry setting in the `HKEY_CURRENT_USER` hive requires that the configuration runs with user credentials, rather than as the system.</span></span> <span data-ttu-id="2a6d1-148">Sie können die **PsDscRunAsCredential**-Eigenschaft verwenden, um die Benutzeranmeldeinformationen für die Konfiguration anzugeben.</span><span class="sxs-lookup"><span data-stu-id="2a6d1-148">You can use the **PsDscRunAsCredential** property to specify user credentials for the configuration.</span></span> <span data-ttu-id="2a6d1-149">Ein Beispiel finden Sie unter [Ausführen von DSC mit Benutzeranmeldeinformationen](../../../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="2a6d1-149">For an example, see [Running DSC with user credentials](../../../configurations/runAsUser.md).</span></span>