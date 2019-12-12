---
title: Erweitern von Eigenschaften für Objekte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 08/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f33ff3e9-213c-44aa-92ab-09450e65c676
caps.latest.revision: 11
ms.openlocfilehash: 3b14007384cca0d0cfa35655aee437adf73b1ff0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364449"
---
# <a name="extending-properties-for-objects"></a>Erweitern Objekteigenschaften

Wenn Sie .NET Framework Objekte erweitern, können Sie den-Objekten Alias Eigenschaften, Code Eigenschaften, Notiz Eigenschaften, Skript Eigenschaften und Eigenschaften Sätze hinzufügen. Die XML-Daten, die diese Eigenschaften definieren, werden in den folgenden Abschnitten beschrieben.

> [!NOTE]
> Die Beispiele in den folgenden Abschnitten stammen aus der standardmäßigen `Types.ps1xml` Types-Datei im PowerShell-Installationsverzeichnis (`$PSHOME`). Weitere Informationen finden Sie unter [about Types. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml).

## <a name="alias-properties"></a>Alias Eigenschaften

Eine Alias Eigenschaft definiert einen neuen Namen für eine vorhandene Eigenschaft.

Im folgenden Beispiel wird die **count** -Eigenschaft dem [System. Array](/dotnet/api/System.Array) -Typ hinzugefügt. Das [aliasproperty](/dotnet/api/system.management.automation.psaliasproperty) -Element definiert die erweiterte Eigenschaft als Alias Eigenschaft. Das [Name](/dotnet/api/system.management.automation.psmemberinfo.name) -Element gibt den neuen Namen an. Und das [referencedmembership Name](/dotnet/api/system.management.automation.psaliasproperty.referencedmembername) -Element gibt die vorhandene Eigenschaft an, auf die vom Alias verwiesen wird. Sie können auch das `AliasProperty`-Element den Membern des Members [-Elements hinzu](/dotnet/api/system.management.automation.psmemberset) fügen.

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

## <a name="code-properties"></a>Code Eigenschaften

Eine Code Eigenschaft verweist auf eine statische Eigenschaft eines .NET Framework Objekts.

Im folgenden Beispiel wird die **Mode** -Eigenschaft dem [System. IO. directoriyinfo](/dotnet/api/System.IO.DirectoryInfo) -Typ hinzugefügt. Das [CodeProperty](/dotnet/api/system.management.automation.pscodeproperty) -Element definiert die erweiterte Eigenschaft als Code Eigenschaft. Das [Name](/dotnet/api/system.management.automation.psmemberinfo.name) -Element gibt den Namen der erweiterten Eigenschaft an. Und das [getcodereferenzierungselement](/dotnet/api/system.management.automation.pscodeproperty.gettercodereference) definiert die statische Methode, auf die von der erweiterten Eigenschaft verwiesen wird. Sie können auch das `CodeProperty`-Element den Membern des Members [-Elements hinzu](/dotnet/api/system.management.automation.psmemberset) fügen.

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

Eine Hinweis Eigenschaft definiert eine Eigenschaft, die über einen statischen Wert verfügt.

Im folgenden Beispiel wird die **Status** -Eigenschaft, deren Wert immer **Erfolg**ist, dem [System. IO. directoriyinfo](/dotnet/api/System.IO.DirectoryInfo) -Typ hinzugefügt. Das [NoteProperty](/dotnet/api/system.management.automation.psnoteproperty) -Element definiert die erweiterte Eigenschaft als Note-Eigenschaft. Das [Name](/dotnet/api/system.management.automation.psmemberinfo.name) -Element gibt den Namen der erweiterten Eigenschaft an. Das [value](/dotnet/api/system.management.automation.psnoteproperty.value) -Element gibt den statischen Wert der erweiterten Eigenschaft an. Das `NoteProperty`-Element kann auch den Membern [des Elements Members](/dotnet/api/system.management.automation.psmemberset) hinzugefügt werden.

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

## <a name="script-properties"></a>Skript Eigenschaften

Eine Skript Eigenschaft definiert eine Eigenschaft, deren Wert die Ausgabe eines Skripts ist.

Im folgenden Beispiel wird die **VERSIONINFO** -Eigenschaft dem [System. IO. FileInfo](/dotnet/api/System.IO.FileInfo) -Typ hinzugefügt. Das [scriptproperty](/dotnet/api/system.management.automation.psscriptproperty) -Element definiert die erweiterte Eigenschaft als Skript Eigenschaft. Das [Name](/dotnet/api/system.management.automation.psmemberinfo.name) -Element gibt den Namen der erweiterten Eigenschaft an. Das [getscriptblock](/dotnet/api/system.management.automation.psscriptproperty.getterscript) -Element gibt das Skript an, das den Eigenschafts Wert generiert. Sie können auch das `ScriptProperty`-Element den Membern des Members [-Elements hinzu](/dotnet/api/system.management.automation.psmemberset) fügen.

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

## <a name="property-sets"></a>Eigenschaften Sätze

Ein Eigenschaften Satz definiert eine Gruppe erweiterter Eigenschaften, auf die durch den Namen des Satzes verwiesen werden kann.
Beispielsweise kann der [Format-Table](/powershell/module/Microsoft.PowerShell.Utility/Format-Table)
**Property** -Parameter eine bestimmte Eigenschaft festlegen, die angezeigt werden soll. Wenn ein Eigenschaften Satz angegeben wird, werden nur die Eigenschaften angezeigt, die zum Satz gehören.

Es gibt keine Einschränkung hinsichtlich der Anzahl der Eigenschafts Sätze, die für ein Objekt definiert werden können. Die Eigenschaften Sätze, die zum Definieren der Standard Anzeigeeigenschaften eines Objekts verwendet werden, müssen jedoch innerhalb des **psstandardmembers** -Element Satzes angegeben werden. In der Datei mit den `Types.ps1xml` Typen enthalten die standardmäßigen Eigenschaften Satz Namen " **defaultdisplayproperty**", " **defaultdisplaypropertyset**" und " **defaultkeypropertyset**". Alle zusätzlichen Eigenschaften Sätze, die Sie dem **psstandardmembers** -Element Satz hinzufügen, werden ignoriert.

Im folgenden Beispiel wird der Wert der **defaultdisplaypropertyset** -Eigenschaft dem **psstandardmembers** -Element Satz des Typs [System. ServiceProcess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) hinzugefügt. Das [PropertySet](/dotnet/api/system.management.automation.pspropertyset) -Element definiert die Gruppe von Eigenschaften. Das [Name](/dotnet/api/system.management.automation.psmemberinfo.name) -Element gibt den Namen des Eigenschaften Satzes an. Und das [referencedproperties](/dotnet/api/system.management.automation.pspropertyset.referencedpropertynames) -Element gibt die Eigenschaften des Satzes an. Sie können auch das `PropertySet`-Element den Membern des [Type](/dotnet/api/system.management.automation.pstypename) -Elements hinzufügen.

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

## <a name="see-also"></a>Siehe auch

[Informationen zu Typen. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)

[System. Management. Automation](/dotnet/api/System.Management.Automation)

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
