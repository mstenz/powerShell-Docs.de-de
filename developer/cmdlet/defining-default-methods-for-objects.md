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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861406"
---
# <a name="defining-default-methods-for-objects"></a>Definieren von Standardmethoden für Objekte

Wenn Sie .NET Framework-Objekten erweitern, können Sie Methoden in Code und Skriptmethoden für die Objekte hinzufügen. Der XML-Code, der verwendet wird, um diese Methoden zu definieren, wird in den folgenden Abschnitten beschrieben.

> [!NOTE]
> In die Beispielen in den folgenden Abschnitten werden aus der Types. ps1xml-Typen-Datei im Installationsverzeichnis von Windows PowerShell (`$pshome`).

## <a name="code-methods"></a>Methoden in Code

Eine Codemethode verweist auf eine statische Methode der .NET Framework-Objekt.

Im folgenden Beispiel die **ConvertLargeIntegerToInt64** -Methode hinzugefügt wird, um die [System.Xml.Xmlnode? Displayproperty = Fullname](/dotnet/api/System.Xml.XmlNode) Typ. Die [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) Element definiert die erweiterte Methode als eine Codemethode. Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) Element gibt den Namen der erweiterten-Methode. Und der [CodeReference](http://msdn.microsoft.com/en-us/70017b85-18d2-4f55-8357-92f309d5618b) Element gibt an, die statische Methode. (Sie können auch hinzufügen der [CodeMethod](http://msdn.microsoft.com/en-us/1ea9b031-bbcf-4e35-b497-bf30fa0b1b05) Element auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)

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

Eine Skriptmethode definiert eine Methode, deren Wert die Ausgabe eines Skripts ist. Im folgenden Beispiel die **ConvertToDateTime** -Methode hinzugefügt wird, um die [System.Management.Managementobject? Displayproperty = Fullname](/dotnet/api/System.Management.ManagementObject) Typ. Die [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) Element definiert die erweiterte Methode als eine Skriptmethode. Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) Element gibt den Namen der erweiterten-Methode. Und der [Skript](http://msdn.microsoft.com/en-us/1937ad1b-bb2b-4512-9864-01fc0767d46f) Element gibt an, das Skript, das den methodenwert generiert. (Sie können auch hinzufügen der [ScriptMethod](http://msdn.microsoft.com/en-us/59f8160f-bc95-42f0-92e2-b16a616bc65c) Element auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)

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