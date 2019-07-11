---
title: Definieren von standardmäßigen Methoden für Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 53fe744a-485f-4c21-9623-1cb546372211
caps.latest.revision: 9
ms.openlocfilehash: af554cde5e888f2a008028010332caa473151622
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733980"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="26d87-102">Definieren von Standardmethoden für Objekte</span><span class="sxs-lookup"><span data-stu-id="26d87-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="26d87-103">Wenn Sie .NET Framework-Objekten erweitern, können Sie Methoden in Code und Skriptmethoden für die Objekte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="26d87-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="26d87-104">Der XML-Code, der verwendet wird, um diese Methoden zu definieren, wird in den folgenden Abschnitten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="26d87-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="26d87-105">In die Beispielen in den folgenden Abschnitten werden aus der Types. ps1xml-Typen-Datei im Installationsverzeichnis von Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="26d87-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="26d87-106">Methoden in Code</span><span class="sxs-lookup"><span data-stu-id="26d87-106">Code Methods</span></span>

<span data-ttu-id="26d87-107">Eine Codemethode verweist auf eine statische Methode der .NET Framework-Objekt.</span><span class="sxs-lookup"><span data-stu-id="26d87-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="26d87-108">Im folgenden Beispiel die **ConvertLargeIntegerToInt64** -Methode hinzugefügt wird, um die [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) Typ.</span><span class="sxs-lookup"><span data-stu-id="26d87-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="26d87-109">Die [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) Element definiert die erweiterte Methode als eine Codemethode.</span><span class="sxs-lookup"><span data-stu-id="26d87-109">The [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element defines the extended method as a code method.</span></span> <span data-ttu-id="26d87-110">Die [Namen](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) Element gibt den Namen der erweiterten-Methode.</span><span class="sxs-lookup"><span data-stu-id="26d87-110">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="26d87-111">Und der [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) Element gibt an, die statische Methode.</span><span class="sxs-lookup"><span data-stu-id="26d87-111">And, the [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) element specifies the static method.</span></span> <span data-ttu-id="26d87-112">(Sie können auch hinzufügen der [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) Element, das Mitglied der [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) Element.)</span><span class="sxs-lookup"><span data-stu-id="26d87-112">(You can also add the [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Xml.XmlNode</Name>
  <Members>
    <CodeMethod>
      <Name>ToString</Name>
      <CodeReference>
        <TypeName>Microsoft.PowerShell.ToStringCodemethods</TypeName>
        <MethodName>XmlNode</MethodName>
      </CodeReference>
    </CodeMethod>
  </Members>
</Type>
```

## <a name="script-methods"></a><span data-ttu-id="26d87-113">Skriptmethoden</span><span class="sxs-lookup"><span data-stu-id="26d87-113">Script Methods</span></span>

<span data-ttu-id="26d87-114">Eine Skriptmethode definiert eine Methode, deren Wert die Ausgabe eines Skripts ist.</span><span class="sxs-lookup"><span data-stu-id="26d87-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="26d87-115">Im folgenden Beispiel die **ConvertToDateTime** -Methode hinzugefügt wird, um die [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) Typ.</span><span class="sxs-lookup"><span data-stu-id="26d87-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="26d87-116">Die [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) Element definiert die erweiterte Methode als eine Skriptmethode.</span><span class="sxs-lookup"><span data-stu-id="26d87-116">The [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element defines the extended method as a script method.</span></span> <span data-ttu-id="26d87-117">Die [Namen](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) Element gibt den Namen der erweiterten-Methode.</span><span class="sxs-lookup"><span data-stu-id="26d87-117">The [Name](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) element specifies the name of the extended method.</span></span> <span data-ttu-id="26d87-118">Und der [Skript](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) Element gibt an, das Skript, das den methodenwert generiert.</span><span class="sxs-lookup"><span data-stu-id="26d87-118">And, the [Script](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) element specifies the script that generates the method value.</span></span> <span data-ttu-id="26d87-119">(Sie können auch hinzufügen der [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) Element, das Mitglied der [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) Element.)</span><span class="sxs-lookup"><span data-stu-id="26d87-119">(You can also add the [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) element to the members of the [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) element.)</span></span>

```xml
<Type>
  <Name>System.Management.ManagementObject</Name>
  <Members>
    <ScriptMethod>
      <Name>ConvertToDateTime</Name>
      <Script>
        [System.Management.ManagementDateTimeConverter]::ToDateTime($args[0])
      </Script>
    </ScriptMethod>
  </Members>
</Type>
```

## <a name="see-also"></a><span data-ttu-id="26d87-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="26d87-120">See Also</span></span>

[<span data-ttu-id="26d87-121">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="26d87-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
