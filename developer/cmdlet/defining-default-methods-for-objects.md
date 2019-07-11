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
# <a name="defining-default-methods-for-objects"></a>Definieren von Standardmethoden für Objekte

Wenn Sie .NET Framework-Objekten erweitern, können Sie Methoden in Code und Skriptmethoden für die Objekte hinzufügen. Der XML-Code, der verwendet wird, um diese Methoden zu definieren, wird in den folgenden Abschnitten beschrieben.

> [!NOTE]
> In die Beispielen in den folgenden Abschnitten werden aus der Types. ps1xml-Typen-Datei im Installationsverzeichnis von Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Methoden in Code

Eine Codemethode verweist auf eine statische Methode der .NET Framework-Objekt.

Im folgenden Beispiel die **ConvertLargeIntegerToInt64** -Methode hinzugefügt wird, um die [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) Typ. Die [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) Element definiert die erweiterte Methode als eine Codemethode. Die [Namen](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) Element gibt den Namen der erweiterten-Methode. Und der [CodeReference](/dotnet/api/system.management.automation.pscodemethod.codereference?view=pscore-6.2.0#System_Management_Automation_PSCodeMethod_CodeReference) Element gibt an, die statische Methode. (Sie können auch hinzufügen der [PSCodeMethod](/dotnet/api/system.management.automation.pscodemethod) Element, das Mitglied der [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) Element.)

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

## <a name="script-methods"></a>Skriptmethoden

Eine Skriptmethode definiert eine Methode, deren Wert die Ausgabe eines Skripts ist. Im folgenden Beispiel die **ConvertToDateTime** -Methode hinzugefügt wird, um die [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) Typ. Die [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) Element definiert die erweiterte Methode als eine Skriptmethode. Die [Namen](/dotnet/api/system.management.automation.psmemberinfo.name?view=pscore-6.2.0#System_Management_Automation_PSMemberInfo_Name) Element gibt den Namen der erweiterten-Methode. Und der [Skript](/dotnet/api/system.management.automation.psscriptmethod.script?view=pscore-6.2.0#System_Management_Automation_PSScriptMethod_Script) Element gibt an, das Skript, das den methodenwert generiert. (Sie können auch hinzufügen der [PSScriptMethod](/dotnet/api/system.management.automation.psscriptmethod?view=pscore-6.2.0) Element, das Mitglied der [PSMemberSets](/dotnet/api/system.management.automation.psmemberset?view=pscore-6.2.0) Element.)

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

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
