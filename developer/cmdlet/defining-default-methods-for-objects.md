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
ms.openlocfilehash: fa0f0371856d8723af7ec17a4306de209a481a18
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068214"
---
# <a name="defining-default-methods-for-objects"></a><span data-ttu-id="22320-102">Definieren von Standardmethoden für Objekte</span><span class="sxs-lookup"><span data-stu-id="22320-102">Defining Default Methods for Objects</span></span>

<span data-ttu-id="22320-103">Wenn Sie .NET Framework-Objekten erweitern, können Sie Methoden in Code und Skriptmethoden für die Objekte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="22320-103">When you extend .NET Framework objects, you can add code methods and script methods to the objects.</span></span> <span data-ttu-id="22320-104">Der XML-Code, der verwendet wird, um diese Methoden zu definieren, wird in den folgenden Abschnitten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="22320-104">The XML that is used to define these methods is described in the following sections.</span></span>

> [!NOTE]
> <span data-ttu-id="22320-105">In die Beispielen in den folgenden Abschnitten werden aus der Types. ps1xml-Typen-Datei im Installationsverzeichnis von Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="22320-105">The examples in the following sections are from the Types.ps1xml types file in the Windows PowerShell installation directory (`$pshome`).</span></span>

## <a name="code-methods"></a><span data-ttu-id="22320-106">Methoden in Code</span><span class="sxs-lookup"><span data-stu-id="22320-106">Code Methods</span></span>

<span data-ttu-id="22320-107">Eine Codemethode verweist auf eine statische Methode der .NET Framework-Objekt.</span><span class="sxs-lookup"><span data-stu-id="22320-107">A code method references a static method of a .NET Framework object.</span></span>

<span data-ttu-id="22320-108">Im folgenden Beispiel die **ConvertLargeIntegerToInt64** -Methode hinzugefügt wird, um die [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) Typ.</span><span class="sxs-lookup"><span data-stu-id="22320-108">In the following example, the **ConvertLargeIntegerToInt64** method is added to the [System.Xml.Xmlnode?Displayproperty=Fullname](/dotnet/api/System.Xml.XmlNode) type.</span></span> <span data-ttu-id="22320-109">Die [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) Element definiert die erweiterte Methode als eine Codemethode.</span><span class="sxs-lookup"><span data-stu-id="22320-109">The [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element defines the extended method as a code method.</span></span> <span data-ttu-id="22320-110">Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) Element gibt den Namen der erweiterten-Methode.</span><span class="sxs-lookup"><span data-stu-id="22320-110">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="22320-111">Und der [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) Element gibt an, die statische Methode.</span><span class="sxs-lookup"><span data-stu-id="22320-111">And, the [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) element specifies the static method.</span></span> <span data-ttu-id="22320-112">(Sie können auch hinzufügen der [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) Element auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)</span><span class="sxs-lookup"><span data-stu-id="22320-112">(You can also add the [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="script-methods"></a><span data-ttu-id="22320-113">Skriptmethoden</span><span class="sxs-lookup"><span data-stu-id="22320-113">Script Methods</span></span>

<span data-ttu-id="22320-114">Eine Skriptmethode definiert eine Methode, deren Wert die Ausgabe eines Skripts ist.</span><span class="sxs-lookup"><span data-stu-id="22320-114">A script method defines a method whose value is the output of a script.</span></span> <span data-ttu-id="22320-115">Im folgenden Beispiel die **ConvertToDateTime** -Methode hinzugefügt wird, um die [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) Typ.</span><span class="sxs-lookup"><span data-stu-id="22320-115">In the following example, the **ConvertToDateTime** method is added to the [System.Management.Managementobject?Displayproperty=Fullname](/dotnet/api/System.Management.ManagementObject) type.</span></span> <span data-ttu-id="22320-116">Die [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) Element definiert die erweiterte Methode als eine Skriptmethode.</span><span class="sxs-lookup"><span data-stu-id="22320-116">The [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element defines the extended method as a script method.</span></span> <span data-ttu-id="22320-117">Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) Element gibt den Namen der erweiterten-Methode.</span><span class="sxs-lookup"><span data-stu-id="22320-117">The [Name](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) element specifies the name of the extended method.</span></span> <span data-ttu-id="22320-118">Und der [Skript](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) Element gibt an, das Skript, das den methodenwert generiert.</span><span class="sxs-lookup"><span data-stu-id="22320-118">And, the [Script](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) element specifies the script that generates the method value.</span></span> <span data-ttu-id="22320-119">(Sie können auch hinzufügen der [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) Element auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)</span><span class="sxs-lookup"><span data-stu-id="22320-119">(You can also add the [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) element to the members of the [MemberSets](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) element.)</span></span>

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

## <a name="see-also"></a><span data-ttu-id="22320-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="22320-120">See Also</span></span>

[<span data-ttu-id="22320-121">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="22320-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)