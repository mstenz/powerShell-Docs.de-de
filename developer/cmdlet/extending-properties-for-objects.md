---
title: Erweitern von Eigenschaften für Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: be31d03b02394cb1694909cf7b65bbc2a29f6976
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795435"
---
# <a name="extending-properties-for-objects"></a>Erweitern Objekteigenschaften

Wenn Sie .NET Framework-Objekten erweitern, können Sie die Eigenschaften, Codeeigenschaften, Note-Eigenschaften, Skripteigenschaften und Eigenschaftensätze alias für die Objekte hinzufügen. Der XML-Code, die zum Definieren der Eigenschaften verwendet wird, wird in den folgenden Abschnitten beschrieben.

> [!NOTE]
> In die Beispielen in den folgenden Abschnitten werden der Standarddatei für die Typen von Types. ps1xml im Installationsverzeichnis von Windows PowerShell (`$pshome`).

## <a name="alias-properties"></a>Aliaseigenschaften

Eine aliaseigenschaft definiert einen neuen Namen für eine vorhandene Eigenschaft.

Im folgenden Beispiel die `Count` Eigenschaft hinzugefügt wird die [System.Array? Displayproperty = Fullname](/dotnet/api/System.Array) Typ. Die [AliasProperty](http://msdn.microsoft.com/en-us/b140038c-807a-4bb9-beca-332491cda1b1) Element definiert die erweiterte Eigenschaft als aliaseigenschaft. Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) Element gibt den neuen Namen. Und der [referencedmembername-Eigenschaft](http://msdn.microsoft.com/en-us/0c5db6cc-9033-4d48-88a7-76b962882f7a) Element gibt an, die vorhandene Eigenschaft, die durch den Alias verwiesen wird. (Sie können auch hinzufügen der [AliasProperty](http://msdn.microsoft.com/en-us/d6647953-94ad-4b0b-af2e-4dda6952dee1) Element auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>
```

## <a name="code-properties"></a>Codeeigenschaften

Eine Eigenschaft verweist auf eine statische Eigenschaft von .NET Framework-Objekt.

Im folgenden Beispiel die `Node` Eigenschaft hinzugefügt wird die [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) Typ. Die [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) Element definiert die erweiterte Eigenschaft als Eigenschaft Code. Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) -Element gibt den Namen der erweiterten Eigenschaft. Und der [GetCodeReference](http://msdn.microsoft.com/en-us/62af34f5-cc22-42c0-9e0c-3bd0f5c1a4a0) -Element definiert die statische Methode, die von der erweiterten Eigenschaft verwiesen wird. (Sie können auch hinzufügen der [CodeProperty](http://msdn.microsoft.com/en-us/59bc4d18-41eb-4c0d-8ad3-bbfa5dc488db) Element auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <CodeProperty>
      <Name>Mode</Name>
      <GetCodeReference>
        <TypeName>Microsoft.PowerShell.Commands.FileSystemProvider</TypeName>
        <MethodName>Mode</MethodName>
      </GetCodeReference>
    </CodeProperty>
  </Members>
</Type>
```

## <a name="note-properties"></a>Eigenschaften notieren

Eine hinweiseigenschaft definiert eine Eigenschaft mit einem statischen Wert an.

Im folgenden Beispiel die `Status` -Eigenschaft (, dessen Wert immer "Success") wurde die [System.IO.Directoryinfo? Displayproperty = Fullname](/dotnet/api/System.IO.DirectoryInfo) Typ. Die [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) -Element definiert die erweiterte Eigenschaft als eine hinweiseigenschaft; die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) -Element gibt den Namen der erweiterten Eigenschaft; und die [Wert](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) Element Gibt an, der statische Wert der erweiterten Eigenschaft. (Die [NoteProperty](http://msdn.microsoft.com/en-us/331e6c50-d703-43f0-89bc-ca9fb97800eb) Element kann auch hinzugefügt werden, auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)

```xml
<Type>
  <Name>System.IO.DirectoryInfo</Name>
  <Members>
    <NoteProperty>
      <Name>Status</Name>
      <Value>Success</Value>
    </NoteProperty>
  </Members>
</Type>
```

## <a name="script-properties"></a>Skripteigenschaften

Eine skripteigenschaft definiert eine Eigenschaft, deren Wert die Ausgabe eines Skripts.

Im folgenden Beispiel die `VersionInfo` Eigenschaft hinzugefügt wird die [System.IO.Fileinfo? Displayproperty = Fullname](/dotnet/api/System.IO.FileInfo) Typ. Die [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) -Element definiert die erweiterte Eigenschaft als eine skripteigenschaft. Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) -Element gibt den Namen der erweiterten Eigenschaft. Und der [GetScriptBlock](http://msdn.microsoft.com/en-us/f3c77546-b98e-4c4e-bbe0-6dfd06696d1c) Element gibt an, das Skript, das den Wert der Eigenschaft generiert. (Sie können auch hinzufügen der [ScriptProperty](http://msdn.microsoft.com/en-us/858a4247-676b-4cc9-9f3e-057109aad350) Element auf die Member des der [Elementgruppen](http://msdn.microsoft.com/en-us/46a50fb5-e150-4c03-8584-e1b53e4d49e3) Element.)

```xml
<Type>
  <Name>System.IO.FileInfo</Name>
  <Members>
    <ScriptProperty>
      <Name>VersionInfo</Name>
      <GetScriptBlock>
        [System.Diagnostics.FileVersionInfo]::GetVersionInfo($this.FullName)
      </GetScriptBlock>
    </ScriptProperty>
  </Members>
</Type>
```

## <a name="property-sets"></a>Eigenschaftensätze

Ein Eigenschaftensatz definiert eine Gruppe von erweiterten Eigenschaften, die durch den Namen des Satzes verwiesen werden kann. Z. B. die `Property` Parameter, der die [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table) Cmdlets können angeben, dass eine bestimmte Eigenschaft festlegen, die angezeigt werden. Wenn ein Eigenschaftensatz angegeben wird, werden nur die Eigenschaften, die zum Satz gehören angezeigt.

Es gibt keine Einschränkung für die Anzahl der Eigenschaftensätze, die für ein Objekt definiert werden können. Jedoch müssen der-Eigenschaft wird verwendet, um die Standardeigenschaften für die Anzeige eines Objekts zu definieren, innerhalb der Elementgruppe PSStandardMembers angegeben werden. In der Datei %% amp;quot;Types.ps1xml%%amp;quot; Typen umfassen die Namen der standardmäßigen Satz DefaultDisplayProperty, DefaultDisplayPropertySet und DefaultKeyPropertySet. Alle zusätzlichen Eigenschaftensätze, die Sie für die Elementgruppe PSStandardMembers hinzufügen, werden ignoriert.

Im folgenden Beispiel wird DefaultDisplayPropertySet Eigenschaftensatz enthalten hinzugefügt, auf die PSStandardMembers Member der [System.Serviceprocess.Servicecontroller? Displayproperty = Fullname](/dotnet/api/System.ServiceProcess.ServiceController) Typ. Die [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) Element definiert die Gruppe von Eigenschaften. Die [Namen](http://msdn.microsoft.com/en-us/b58e9d21-c8c9-49a5-909e-9c1cfc64f873) Element gibt den Namen des Eigenschaftensatzes an. Und der [ReferencedProperties](http://msdn.microsoft.com/en-us/5e620423-8679-4fbf-b6db-9f79288e4786) Element gibt die Eigenschaften des Satzes an. (Sie können auch hinzufügen der [PropertySet](http://msdn.microsoft.com/en-us/14cdc234-796e-4857-9b51-bdbaa1412188) Element, das Mitglied der [Typ](http://msdn.microsoft.com/en-us/e5dbd353-d6b2-40a1-92b6-6f1fea744ebe) Element.)

```xml
<Type>
  <Name>System.ServiceProcess.ServiceController</Name>
  <Members>
    <MemberSet>
      <Name>PSStandardMembers</Name>
      <Members>
        <PropertySet>
           <Name>DefaultDisplayPropertySet</Name>
           <ReferencedProperties>
            <Name>Status</Name
            <Name>Name</Name>
            <Name>DisplayName</Name>
          </ReferencedProperties>
        </PropertySet>
      </Members>
    </MemberSet>
  </Members>
</Type>
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
